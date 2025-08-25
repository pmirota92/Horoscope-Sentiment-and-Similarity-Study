# Are All Horoscopes Positive?  
### A 3-Year Sentiment & Similarity Study Across the Zodiac

> **TL;DR:**  
> I scraped 3 years of daily horoscopes for all 12 zodiac signs (English), analyzed sentiment using **VADER** and **Hugging Face transformers**, and measured text similarity using **paraphrase-multilingual-MiniLM-L12-v2** embeddings with **cosine similarity**. I built sign-level time series and word clouds, and tested whether “happiness is pre-programmed” by zodiac.  
> Results: while most horoscopes are indeed positive or neutral, **two signs show significantly higher negative rates**, disproving the idea that *all* horoscopes are uniformly uplifting. Additionally, the texts are highly repetitive: many daily horoscopes resemble earlier ones almost verbatim.

---

## Project Motivation
Years ago, I asked myself a simple question:  

**“Are all horoscopes always positive or neutral?”**  

This project is my attempt to finally answer it with data. By scraping and analyzing horoscopes over three years, I explored whether negativity ever appears, whether some signs receive more “bad luck” than others, and how much of the content is reused.

---

## Key Questions & Hypotheses
1. **Sentiment distribution:** Are horoscopes overwhelmingly positive/neutral, or do negative ones occur?  
   - **H₀:** All horoscopes are positive/neutral.  
   - **H₁:** Some horoscopes contain negativity.  

2. **Sign-level differences:** Do certain signs receive more negative horoscopes?  
   - If yes, is “misfortune” pre-assigned, or explained by outliers?  

3. **Repetition:** Are horoscopes genuinely unique each day, or do they recycle similar content?  

4. **Focus signs:** For **Capricorn** and **Leo** (my two favorites), how does positivity/negativity evolve compared to other signs?

---

## Data & Scope
- **Source:** Scraped from an online horoscope website.  
- **Coverage:** 3 full years of daily horoscopes × 12 zodiac signs, in English.  
- **Granularity:** One text per sign per day (occasional missing entries handled).  
- **Storage:** Cleaned text + metadata (date, sign, sentiment labels, embeddings, similarity scores).  
- **Ethics:** Public content only; no personal data.

---

## Methodology Overview
- **Scraping & Collection:** Automated daily scraping with caching; stored by sign and date.  
- **Preprocessing:** Normalize text (lowercasing, lemmatization, removing boilerplate like “today” or “zodiac”).  
- **Sentiment Analysis:**  
  - **VADER** → fast rule-based scoring.  
  - **Hugging Face transformer model** → refined classification into **positive, neutral, or negative**.  
- **Visualization:**  
  - **Word clouds**: common words in positive vs. negative texts per sign.  
  - **Bar charts**: total sentiment counts per sign over 3 years.  
  - **Time series**: rolling positivity/negativity rates.  
- **Statistical Testing:** Chi-square tests across signs; post-hoc analysis to identify which signs drive differences.  
- **Similarity Analysis:**  
  - Sentence embeddings with **paraphrase-multilingual-MiniLM-L12-v2**.  
  - **Cosine similarity** used to measure overlap with prior horoscopes.  

---

## Analysis Plan (Step-by-Step)
1. **Scrape Data** → daily texts for each sign over 3 years.  
2. **Clean Text** → remove boilerplate, tokenize, lemmatize.  
3. **Sentiment Classification** → label each horoscope using **VADER** and **Hugging Face model**.  
4. **EDA** → distribution of sentiment, missing entries, daily/monthly aggregates.  
5. **Visualization** → word clouds, bar plots, rolling averages.  
6. **Statistical Tests** → check if negativity is evenly distributed across signs.  
7. **Similarity Analysis** → compute embeddings with **MiniLM-L12-v2** and cosine similarity.  
8. **Capricorn & Leo Focus** → compare their positivity/negativity timelines with other signs.  
9. **Reporting** → synthesize findings, add caveats, summarize implications.

---

## Results
- **Sentiment Totals by Sign (3 years)**  
- **Word Clouds**: Positive vs. Negative, per sign  
- **Time Series**: Rolling positivity and negativity per sign  
- **Capricorn & Leo Comparisons**: Positivity/negativity vs. others  
- **Similarity Heatmaps**: Reuse of past horoscopes

**Headline findings:**  
- Most horoscopes are **positive or neutral**, confirming the stereotype.  
- However, **two signs** receive a statistically higher share of negative predictions.  
- This means “misfortune” is **not pre-programmed** equally across signs.  
- Text reuse is common: using embeddings + cosine similarity, I found a high probability that a new horoscope is very similar to a past one.

---

## Capricorn & Leo Highlights
For **Capricorn** and **Leo** I tracked positivity/negativity over time compared to other signs:  
- Showed when they were more/less positive than average.  
- Revealed periods of unusual negativity.  
- Illustrated how individual signs trend against the overall baseline.

---

## Statistical Testing
- **Chi-square tests** → confirmed significant differences across signs.  
- **Post-hoc analysis** → identified **two outlier signs** driving the negativity effect.  
- **Bootstrapping** → computed confidence intervals for per-sign negativity rates.  

---

## Similarity Analysis
- **Embeddings:** Generated with **paraphrase-multilingual-MiniLM-L12-v2** (Sentence Transformers).  
- **Cosine similarity:** Compared each horoscope with all previous ones for the same sign.  
- **Result:** Strong likelihood (>70%) that a horoscope closely resembles at least one earlier text → suggests templated or recycled writing.

---

## Limitations
- Sentiment models may misclassify horoscope-style language.  
- Results reflect **one website’s editorial choices**, not astrology in general.  
- Horoscopes are short → small text changes can flip sentiment.  
- This project is **descriptive**, not causal.  

---

## Future Work
- Scrape multiple sources for comparison.  
- Use domain-adapted sentiment models.  
- Apply **topic modeling** to detect recurring themes.  
- Build an **interactive dashboard** (e.g., Streamlit) to explore trends by sign/date.  

---

## Skills Demonstrated
- **Web scraping & automation**  
- **NLP preprocessing** (cleaning, tokenization, lemmatization)  
- **Sentiment analysis** with **VADER** + **Hugging Face transformers**  
- **Semantic similarity** with **MiniLM embeddings + cosine similarity**  
- **Statistical testing** (chi-square, post-hoc, bootstrapping)  
- **Visualization** (word clouds, timelines, bar plots)  
- **Reproducible project design** (modular, config-driven)  
- **Data storytelling** for both technical and non-technical audiences  

---

