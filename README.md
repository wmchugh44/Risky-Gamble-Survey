# Risk Preference Survey - Streamlit App

A comprehensive risk preference survey based on Tversky & Kahneman (1992), built with Streamlit for online deployment.

## Features

### Core Survey Functionality
- **Clear Gamble Descriptions**: Each prospect is displayed in plain language (e.g., "25% chance to win $100, 75% chance to win nothing")
- **Two-Phase Design**: 
  - Phase 1: Broad sweep across 7 sure amounts
  - Phase 2: Zoomed-in set based on Phase 1 responses
- **Manual Choice Selection**: Users manually choose "Prefer Gamble" vs "Prefer Sure $X" on every row
- **Complete Coverage**: 10 prospect problems covering both gain and loss domains

### Monotonicity Enforcement
- **Instant Validation**: Monotonic consistency is checked on every click, not just at submission
- **Clear Error Messages**: Violations are explained in plain language with reference to Tversky & Kahneman (1992)
- **Automatic Reset**: Invalid selections are immediately reset with explanation
- **No Progression**: Users cannot continue until all rows are answered consistently

### Display & Ordering
- **Gains Domain**: Rows ordered ascending (small → large amounts)
- **Loss Domain**: Rows ordered descending by magnitude (closest to $0 first)
- **Expected Value**: Displayed for each gamble
- **Certainty Equivalent**: Computed from switch point
- **Risk Attitude**: Automatically classified as Averse/Seeking/Neutral

### Results & Export
- **Progress Tracking**: Visual progress bar throughout survey
- **Participant Info**: Name and age collection
- **Multiple Export Formats**: JSON and CSV download options
- **Comprehensive Data**: All choices, computed metrics, and classifications

## Technical Implementation

### Clean Architecture
- ✅ No `st.rerun()` in callbacks (eliminates yellow warnings)
- ✅ Proper state initialization before component rendering
- ✅ Clean error message formatting
- ✅ Monotonicity enforcement with immediate feedback

### Deployment Ready
- Streamlit Cloud compatible
- Minimal dependencies
- Responsive design
- Build version tracking

## Installation & Local Development

### Prerequisites
- Python 3.8+
- pip

### Setup
```bash
# Clone the repository
git clone <your-repo-url>
cd risk-preference-survey

# Install dependencies
pip install -r requirements.txt

# Run locally
streamlit run risk_survey_consolidated_v1_2.py
```

### Local Access
Open your browser to `http://localhost:8501`

## Deployment to Streamlit Cloud

### Step 1: GitHub Setup
1. Push your code to a GitHub repository
2. Ensure `risk_survey_consolidated_v1_2.py` is in the root directory
3. Ensure `requirements.txt` is in the root directory

### Step 2: Streamlit Cloud Deployment
1. Go to [share.streamlit.io](https://share.streamlit.io)
2. Sign in with GitHub
3. Click "New app"
4. Select your repository
5. Set main file path: `risk_survey_consolidated_v1_2.py`
6. Click "Deploy"

### Step 3: Access Your App
Your app will be available at: `https://[your-app-name].streamlit.app`

## Survey Flow

### 1. Introduction
- Participant information collection (name, age)
- Clear instructions about the two-phase design

### 2. Phase 1 (Broad Sweep)
- 7 sure amounts spanning the range
- Gains: ascending order ($10, $20, ..., $90)
- Losses: descending by magnitude (-$10, -$20, ..., -$90)

### 3. Phase 2 (Refined)
- 7 sure amounts zoomed into the switch region from Phase 1
- Same ordering principles as Phase 1

### 4. Results
- Automatic computation of certainty equivalents
- Risk attitude classification
- Data export options

## Monotonicity Logic

Based on Tversky & Kahneman (1992):

### Gain Domain
- If you prefer the gamble over amount X, you must prefer it over any smaller amount
- If you prefer amount X over the gamble, you must prefer any larger amount

### Loss Domain  
- If you prefer the gamble over paying amount X, you must prefer it over paying any smaller amount
- If you prefer paying amount X to avoid the gamble, you must prefer paying any larger amount

## Build Information

Current build: `consolidated-robust-2.0`

## Troubleshooting

### Common Issues
1. **App won't start**: Check that all dependencies are installed
2. **Deployment fails**: Ensure main file path is correct in Streamlit Cloud
3. **Data not saving**: Check browser localStorage (data persists in session)

### Support
For issues or questions, please check the code comments or create an issue in the repository.

## Academic Reference

This implementation is based on:
Tversky, A., & Kahneman, D. (1992). Advances in prospect theory: Cumulative representation of uncertainty. Journal of Risk and Uncertainty, 5(4), 297-323.