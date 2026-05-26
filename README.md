# HireVision
**AI-Powered Resume Screening & Ranking System**

HireVision is an intelligent, automated resume screening system designed to streamline the recruitment process. By leveraging Natural Language Processing (NLP) and Large Language Models (LLMs), it analyzes applicant resumes against job descriptions to provide semantic matching, skill extraction, and automated candidate ranking.

## Features

* **Single Candidate Deep Dive:** Upload a single PDF resume and a job description to get a comprehensive match analysis.
* **Batch Resume Ranking:** Upload multiple resumes simultaneously. The system evaluates all candidates and outputs a ranked leaderboard based on a custom composite score.
* **Intelligent Skill Extraction:** Utilizes `SkillNer` and `spaCy` to autonomously identify and extract technical and soft skills from raw resume text.
* **Semantic Match Scoring:** Uses Sentence Transformers (`all-MiniLM-L6-v2`) to understand the contextual similarity between a candidate's background and the job requirements.
* **Automated Summarization:** Generates a concise candidate profile summary using Hugging Face's BART model (`facebook/bart-large-cnn`).
* **Modern UI:** Built with Gradio, featuring interactive data tables, visual match doughnut charts, and detailed breakdowns of missing vs. matched skills.
* **Data Export:** Easily export candidate rankings and analysis data to CSV format.

## Technologies Used

* **Python 3**
* **Gradio:** For the interactive web interface
* **spaCy:** For tokenization and Named Entity Recognition (NER)
* **SkillNer:** For specialized skill extraction from text
* **Sentence Transformers:** For calculating semantic similarity embeddings
* **Hugging Face Transformers:** For abstractive text summarization
* **pdfplumber:** For reliable text extraction from PDF documents
* **Pandas & NumPy:** For data manipulation, scoring, and ranking

## Installation & Setup

1. **Clone the repository:**
    ```bash
    git clone [https://github.com/your-username/HireVision.git](https://github.com/your-username/HireVision.git)
    cd HireVision
    ```

2. **Install the required dependencies:**
    ```bash
    pip install gradio pdfplumber spacy skillNer sentence_transformers transformers pandas numpy
    ```

3. **Download the required spaCy language model:**
    ```bash
    python -m spacy download en_core_web_lg
    ```

## Usage

1. Run the application:
    ```bash
    python app.py
    ```

*(Note: If running from the Jupyter Notebook, simply execute all cells).*
2. Open the local link provided by Gradio in your web browser.
3. Choose either **Single Resume Analysis** or **Batch Resume Ranking** from the top tabs.
4. Upload the candidate PDF(s) and paste the target Job Description.
5. Click **Analyze** to generate the AI-driven report and rankings.

## How the Scoring Works

The system calculates a **Composite Score** to rank candidates, weighted as follows:

* **60% Semantic Similarity:** How well the context of the resume aligns with the job description.
* **40% Skill Match:** The exact percentage of required skills found in the applicant's extracted skill set.
