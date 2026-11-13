# Data

## `Tweets.csv` — Twitter US Airline Sentiment

The Kaggle *Twitter US Airline Sentiment* dataset: tweets directed at six US
airlines, each labelled by human contributors. It is the ground truth the
sentiment scoring is validated against.

| Property | Value |
| --- | --- |
| Rows | 14,640 tweets |
| Columns | 15 |
| Period | 16–24 February 2015 (9 calendar days, 181 hourly buckets) |
| Airlines | United, US Airways, American, Southwest, Delta, Virgin America |
| Labels | negative 62.7% · neutral 21.2% · positive 16.1% |

### Columns used in this analysis

| Column | Notes |
| --- | --- |
| `tweet_id` | Unique identifier |
| `airline_sentiment` | **Human label** — `negative` / `neutral` / `positive`. The ground truth. |
| `airline_sentiment_confidence` | Annotator agreement, 0–1 |
| `negativereason` | Complaint category where sentiment is negative |
| `airline` | One of the six carriers |
| `text` | Tweet body — the input to VADER and TextBlob |
| `tweet_created` | Timestamp, used for the hourly aggregation |
| `retweet_count`, `name`, `tweet_coord`, `tweet_location`, `user_timezone` | Present but not used here |

### Tweets per airline

| Airline | Tweets |
| --- | ---: |
| United | 3,822 |
| US Airways | 2,913 |
| American | 2,759 |
| Southwest | 2,420 |
| Delta | 2,222 |
| Virgin America | 504 |

### Top complaint categories

| Reason | Count |
| --- | ---: |
| Customer Service Issue | 2,910 |
| Late Flight | 1,665 |
| Can't Tell | 1,190 |
| Cancelled Flight | 847 |
| Lost Luggage | 724 |

**Note.** These are real public tweets, including account names, and the file is
redistributed as published on Kaggle. Nothing was added to it.

---

## Live news data — NewsAPI

Section 1 of the notebook pulls recent English-language articles matching
`"airline"` from [newsapi.org](https://newsapi.org) and scores them with the
same VADER method. The pull is written to `news_live_pull_<date>.csv`, which is
git-ignored because it changes every run and is not part of the analysis.

Requires a free API key in `.env` — see `.env.example`.
