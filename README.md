# FRC Event Data Fetcher 🤖

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![FRC](https://img.shields.io/badge/FRC-Data%20Analysis-red)](https://www.firstinspires.org/robotics/frc)

## 📋 Overview

The FRC Event Data Fetcher is a Python tool designed to aggregate and analyze FIRST Robotics Competition (FRC) team performance data. It pulls data from multiple sources including The Blue Alliance (TBA) and Statbotics APIs to create comprehensive Excel reports for event analysis and scouting purposes.

## ✨ Features

- **Multi-source Data Aggregation**: Fetches data from TBA and Statbotics APIs
- **Historical Analysis**: Retrieves multiple years of team performance data
- **EPA Statistics**: Includes Expected Points Added (EPA) metrics and rankings
- **Awards Tracking**: Compiles team awards across events and years
- **Excel Export**: Generates organized Excel spreadsheets for easy analysis
- **Parallel Processing**: Utilizes multi-threading for faster data retrieval
- **Caching System**: Reduces API calls through intelligent caching
- **Progress Tracking**: Real-time progress updates during data fetching

## 🚀 Quick Start

### Prerequisites

- Python 3.8 or higher
- API keys for The Blue Alliance
- pip (Python package manager)

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/wjxc-workspace/FRC_Event_Data_Fetcher.git
cd FRC_Event_Data_Fetcher
```

2. **Install required packages**
```bash
pip install -r requirements.txt
```

3. **Set up environment variables**
Create a `.env` file in the project root:
```env
TBA_API_KEY=your_tba_api_key_here
FIRST_API_USERNAME=your_first_username (optional)
FIRST_API_AUTH_TOKEN=your_first_token (optional)
```

### Getting API Keys

#### The Blue Alliance API Key
1. Visit [The Blue Alliance Account Page](https://www.thebluealliance.com/account)
2. Sign in with your Google/Apple account
3. Scroll to "Read API Keys" section
4. Generate a new API key
5. Copy the key to your `.env` file

#### FIRST API Token
1. Visit [FIRST API Register Page](https://frc-events.firstinspires.org/services/api/register)
2. Fill the form and click the "Register" button
3. Get the API token
4. Copy the token to your `.env` file


## 📖 Usage

### Basic Usage

Run the script from the command line:
```bash
python frc_data_fetcher.py
```

You'll be prompted for:
- **Event year**: The competition year (e.g., 2024)
- **Event code**: The event identifier (e.g., txhou, casj, micmp)
- **Your team number**: Optional - your FRC team number for reference
- **Years of history**: How many years of historical data to fetch (1-10)

### Example Session
```
=== FRC Event Data Fetcher ===
Event year: 2024
Event code (e.g., txhou, casj): txhou
Your team number (optional, press Enter to skip): 7130
Years of history to fetch (1-10): 3

Fetching teams for 2024txhou...
Found 32 teams: [118, 1255, 2585, 2587, 2882]...
✗ Your team (7130) is not registered for this event

Fetching data for 36 teams...
Progress: 36/36 teams (100.0%)

✓ Data export complete: 2024txhou.xlsx
```

## 📊 Output Format

The tool generates an Excel file named `{year}{event_code}.xlsx` with the following structure:

| Team | 2022 EPA | 2022 Rank | 2022 Awards | 2023 EPA | 2023 Rank | 2023 Awards | 2024 EPA | 2024 Rank | 2024 Awards |
|------|----------|-----------|-------------|----------|-----------|-------------|----------|-----------|-------------|
| 118  | 51.04 | 23 | 2022txirv - Excellence in Engineering Award | 67.82 | 30 | 2023txhou - District Event Winner | 40.98 | 77 | 2024txkat - District Event Winner |

## 🔧 Configuration

### Advanced Settings

You can modify these settings in the code:

```python
# In FRCDataFetcher.export_to_excel()
max_workers = 5  # Number of parallel threads for data fetching

# Cache settings
self._cache = {}  # In-memory cache for API responses
```

### API Rate Limits

- **TBA API**: 10,000 requests per hour
- **Statbotics**: No official rate limit, but be respectful
- The tool implements caching to minimize API calls

## 📁 Project Structure

```
frc-data-fetcher/
├── frc_data_fetcher.py    # Main script
├── requirements.txt        # Python dependencies
├── .env                   # Environment variables (create this)
├── .gitignore            # Git ignore file
├── README.md             # Project documentation
└── output/               # Generated Excel files
```

## 🛠️ Troubleshooting

### Common Issues

#### API Key Errors
```
ValueError: TBA_API_KEY not found in environment variables
```
**Solution**: Ensure your `.env` file exists and contains valid API keys

#### Network Connection Issues
```
RuntimeError: Could not fetch teams for event 2024txhou
```
**Solution**: Check your internet connection and verify the event code is correct

#### Invalid Event Code
```
No teams found for event
```
**Solution**: Verify the event code format (year + event code, e.g., "2024txhou")

#### Missing Data
Some teams show "N/A" for EPA or ranks
**Solution**: This is normal for teams that didn't compete in certain years

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Setup

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run tests (if available)
python -m pytest tests/
```

## 📈 Future Enhancements

- [ ] GUI interface using tkinter or PyQt
- [ ] Support for district rankings
- [ ] Integration with more data sources
- [ ] Customizable export formats (CSV, JSON)
- [ ] Team comparison visualizations
- [ ] Web interface using Flask/FastAPI

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [The Blue Alliance](https://www.thebluealliance.com/) for their comprehensive FRC data API
- [Statbotics](https://www.statbotics.io/) for advanced statistical analysis
- [FIRST Robotics Competition](https://www.firstinspires.org/robotics/frc) for inspiring STEM education
- All FRC teams and volunteers who make this community amazing

## 📞 Support

For issues, questions, or suggestions:
- Open an issue on [GitHub Issues](https://github.com/yourusername/frc-data-fetcher/issues)
- Contact the maintainers

**Built with ❤️ for the FRC Community**

*Last Updated: August 2025*