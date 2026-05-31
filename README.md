# AGIS v1.5 - AKSA Genset Information System

## Overview

AGIS (AKSA Genset Information System) is an accuracy-first Retrieval Augmented Generation (RAG) platform designed to provide reliable technical answers directly from genset and engine datasheets.

The system uses vector search and Large Language Models (LLMs) to retrieve relevant technical information while minimizing hallucinations. AGIS is intended to function as an engineering knowledge retrieval system rather than a general-purpose chatbot.

---

## Problem Statement

Engineering datasheets often contain hundreds of technical specifications, ratings, dimensions, protection systems, and operational parameters. Finding specific information manually can be time-consuming and error-prone.

AGIS solves this problem by allowing users to ask natural language questions and receive answers grounded only in the uploaded technical documentation.

---

## Key Features

### Accuracy-First Architecture

* Answers only from uploaded datasheets
* Hallucination control
* No assumptions or fabricated specifications
* Datasheet-grounded responses

### Multi-Document Knowledge Base

Current supported documents:

* AKSA AC3000 Genset Datasheet
* Cummins QSK78-G9 Engine Datasheet

### Section-Aware Chunking

Custom chunking strategy developed for engineering documents:

* Description
* Features
* Engine Data
* Ratings
* Fuel Consumption
* Cooling System Data
* Weight & Dimensions

This ensures that critical tables and numerical values remain intact during retrieval.

### Vector Search

* Gemini Embeddings
* Qdrant Vector Database
* Semantic Retrieval

### Technical Question Answering

Examples:

* What is the engine displacement?
* What is the bore and stroke?
* What cooling system is used?
* What certificates does AC3000 have?
* What is the fuel consumption at 75% load?

---

## System Architecture

User Question
↓
Question & Answer Chain
↓
Qdrant Retriever
↓
Qdrant Vector Database
↓
Relevant Datasheet Chunks
↓
Gemini LLM
↓
Grounded Technical Answer

---

## Knowledge Ingestion Pipeline

Datasheet PDF
↓
Text Extraction
↓
Metadata Processing
↓
Section-Based Chunking
↓
Gemini Embeddings
↓
Qdrant Storage

---

## Technologies Used

### Workflow Orchestration

* n8n

### Artificial Intelligence

* Google Gemini
* Gemini Embeddings

### Vector Database

* Qdrant

### Programming

* JavaScript

### Knowledge Retrieval

* Retrieval Augmented Generation (RAG)

---

## Metadata Strategy

Each chunk is enriched with metadata such as:

* Manufacturer
* Genset Model
* Engine Model
* Document Type
* Section Name
* Source Document

This improves retrieval precision and future scalability.

---

## Validation

AGIS was validated using multiple engineering questions covering:

* Engine Specifications
* Cooling System Information
* Ratings and Certifications
* Fuel Consumption Data
* Protection Systems
* Dimensions and Weight

The system successfully retrieves and answers technical questions directly from datasheet content.

---

## Challenges Solved

### Engineering Table Preservation

A major challenge in technical RAG systems is preventing table fragmentation during chunking.

AGIS uses section-aware chunking to ensure that:

* Fuel consumption tables remain intact
* Ratings tables remain intact
* Numerical values are preserved
* Retrieval accuracy is maintained

### Hallucination Reduction

The system is configured to return:

"Information not available in datasheet."

whenever relevant information cannot be retrieved from the uploaded documents.

---

## Future Roadmap

### AGIS v3

Planned improvements:

* Source Citations
* Section Retrieval Mode
* Multi-Genset Support
* Additional Engine Datasheets
* Alternator Datasheet Integration
* Web Interface
* Deployment

---

## Project Author

Tasdiq Ayub

Electrical Engineer | AI Automation Builder | n8n Workflow Developer

---

## Disclaimer

AGIS is intended as an engineering knowledge retrieval system. Responses are generated from uploaded technical documentation and should be verified against official manufacturer datasheets for critical engineering decisions.
