# AI-Based IT Ticket Resolution and LLM Auto-Responder

## Project Overview

This project analyzes IT support tickets based on their issue category and resolution time. Machine learning clustering is used to group tickets according to their resolution characteristics.

The project also implements an AI-based IT support auto-responder. A technical knowledge base is created containing common IT problems and their approved troubleshooting solutions. When a user enters an IT problem, the system uses semantic similarity to find the most relevant troubleshooting guide and generates a suitable support response using an LLM.

## Problem Statement

Cluster and classify IT ticket resolution times, and implement an LLM auto-responder that matches user technical issues against knowledge base resolution guides.

## Objectives

* Analyze IT support ticket resolution times.
* Classify tickets into Fast, Medium, and Slow resolution categories.
* Cluster IT tickets using K-Means clustering.
* Measure clustering quality using the Silhouette Score.
* Create a technical IT knowledge base.
* Match user problems with relevant knowledge-base guides.
* Generate AI-based troubleshooting responses.
* Provide a confidence level for the matched solution.
* Provide a fallback response when no reliable knowledge-base match is found.

## Technologies Used

* Python
* Google Colab
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* Sentence Transformers
* Hugging Face Transformers
* FLAN-T5
* K-Means Clustering
* Cosine Similarity

## System Workflow

```text
IT Support Tickets
        |
        v
Data Preprocessing
        |
        v
Resolution Time Classification
        |
        v
Feature Scaling
        |
        v
K-Means Clustering
        |
        v
Cluster Analysis
        |
        +----------------------+
        |                      |
        v                      v
Knowledge Base           User IT Problem
        |                      |
        |                      v
        |              Sentence Embedding
        |                      |
        |                      v
        |              Cosine Similarity
        |                      |
        +-----------> Best Matching Guide
                               |
                               v
                       Confidence Check
                               |
                               v
                         LLM Response
                               |
                               v
                       IT Support Reply
```

## Part 1: IT Ticket Analysis

The project uses IT support ticket information such as:

* Ticket ID
* Issue
* Category
* Resolution Time

Resolution time is classified into three groups:

* **Fast:** Less than 4 hours
* **Medium:** 4 to 10 hours
* **Slow:** More than 10 hours

### K-Means Clustering

K-Means clustering is applied using:

* Resolution time
* Encoded ticket category

The data is standardized before clustering.

The project uses three clusters to identify groups of tickets with similar resolution characteristics.

### Silhouette Score

The Silhouette Score is calculated to evaluate the quality of the generated clusters.

## Part 2: Knowledge Base

A technical knowledge base is created for common IT problems such as:

* Password reset
* WiFi connection problem
* VPN connection failure
* Printer problem
* Email not working
* Computer running slow
* Software installation
* Blue screen error

Each knowledge-base entry contains:

* Problem title
* Problem description
* Approved troubleshooting solution

## Part 3: Semantic Issue Matching

Sentence Transformers are used to convert the knowledge-base content and user problem into numerical embeddings.

Cosine similarity is then used to identify the most relevant troubleshooting guide.

The system assigns a confidence level:

* **High:** Similarity score >= 0.70
* **Medium:** Similarity score >= 0.50
* **Low:** Similarity score < 0.50

If the confidence is Low, the system does not generate an unsupported solution and instead recommends contacting IT support.

## Part 4: LLM Auto-Responder

The project uses the FLAN-T5 language model to generate a natural-language IT support response.

The LLM receives:

* User's technical issue
* Approved knowledge-base solution

The generated response is restricted to the approved troubleshooting information.

This helps reduce the possibility of generating unrelated troubleshooting instructions.

## Example

### User Input

```text
My VPN is not connecting to the company network.
```

### Matched Guide

```text
VPN Connection Failure
```

### Confidence

```text
High
```

### AI Support Response

```text
Here are the recommended troubleshooting steps:

Check your internet connection, restart the VPN client, verify your company credentials, and reconnect. If the VPN server is unavailable, contact IT support.
```

## Project Outputs

The project generates the following files:

### `it_ticket_cluster_report.csv`

Contains the ticket clustering and resolution analysis results.

### `IT_knowledge_base.csv`

Contains the technical problems and approved troubleshooting solutions.

### `IT_AutoResponder_Test_Results.csv`

Contains test cases, matched knowledge-base guides, confidence levels, and generated support responses.

## How to Run

### Step 1: Open Google Colab

Open the notebook:

```text
IT_Ticket_Analyzer.ipynb
```

### Step 2: Install Required Libraries

Run the installation cell provided in the notebook.

### Step 3: Run the Notebook

Run the cells from top to bottom.

The notebook performs:

1. Dataset creation
2. Resolution classification
3. Feature encoding
4. Feature scaling
5. K-Means clustering
6. Silhouette score calculation
7. Cluster visualization
8. Knowledge-base creation
9. Sentence embedding generation
10. Semantic similarity matching
11. LLM response generation
12. Auto-responder testing
13. CSV report generation

### Step 4: Test the Auto-Responder

Example inputs:

```text
I forgot my password and cannot login
```

```text
My office WiFi is not connecting
```

```text
The printer is offline and won't print
```

```text
My computer is extremely slow
```

```text
I cannot send or receive emails
```

```text
The VPN connection keeps failing
```

## Project Structure

```text
IT-Ticket-Resolution-LLM/
│
├── IT_Ticket_Analyzer.ipynb
├── it_ticket_cluster_report.csv
├── IT_knowledge_base.csv
├── IT_AutoResponder_Test_Results.csv
└── README.md
```

## Key Features

* IT ticket resolution-time classification
* K-Means clustering
* Silhouette Score evaluation
* Knowledge-base creation
* Semantic similarity search
* Confidence-based matching
* LLM-generated IT support responses
* Low-confidence fallback handling
* CSV-based result reports

## Limitations

* The demonstration dataset is small and sample-based.
* The knowledge base contains a limited number of IT problems.
* The quality of generated responses depends on the knowledge-base content and language model.
* Real-world deployment would require a larger organization-specific ticket dataset and knowledge base.

## Future Enhancements

* Connect the system to a real IT service-management database.
* Add more technical troubleshooting guides.
* Add a web-based user interface.
* Store historical ticket data automatically.
* Use advanced retrieval-augmented generation (RAG).
* Add authentication and role-based access.
* Add real-time ticket creation and tracking.
* Improve confidence calibration using real support data.

## Conclusion

This project combines machine learning, semantic search, and large language models to analyze IT support tickets and provide automated troubleshooting assistance.

The system first analyzes historical ticket resolution patterns and then uses a knowledge base to identify the most relevant solution for a new user problem. An LLM converts the approved solution into a natural IT support response while a confidence mechanism provides a fallback when a reliable match cannot be found.
