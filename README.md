# Student Math Marks Prediction

An end-to-end Machine Learning web application designed to predict a student's math exam score based on demographic factors, parental education level, lunch status, test preparation course status, and other exam scores (reading and writing).

## Features
- **Exploratory Data Analysis (EDA):** Notebooks for data visualization and analysis of key features affecting student performance.
- **Modular Pipeline:** Separate scripts for data ingestion, feature transformation, model training, and model prediction.
- **Model Evaluation:** Evaluates multiple regressors (Random Forest, Decision Tree, Gradient Boosting, Linear Regression, XGBoost, CatBoost, AdaBoost, and K-Neighbors) and automatically exports the model with the highest R^2 score.
- **Web App Interface:** A Flask-based web application to input features and receive real-time predictions.

## Project Structure
```text
├── .ebextensions/              # AWS Elastic Beanstalk configuration files
├── artifacts/                  # Trained model and preprocessor artifacts
├── notebooks/                  # Jupyter notebooks for EDA and model training
├── src/                        # Core source code package
│   ├── components/             # Ingestion, transformation, and trainer modules
│   ├── pipeline/               # Training and prediction orchestration pipelines
│   ├── exception.py            # Custom exception handling with traceback capture
│   ├── logger.py               # Custom logger for timestamped execution logs
│   └── utils.py                # Helper functions for serialization and evaluation
├── template/                   # HTML templates for the Flask web application
├── application.py              # Flask app entry point (configured for AWS)
├── requirements.txt            # Project dependencies
└── setup.py                    # Project packaging configuration
```

## Getting Started

### Prerequisites
- Python 3.8+ (Python 3.13 recommended)
- Conda or virtualenv

### Installation & Local Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/umerkang66/car-price-prediction-aws.git
   cd math_marks_prediction
   ```

2. **Create and activate a virtual environment:**
   ```bash
   conda create --prefix ./venv python=3.13 -y
   conda activate ./venv
   ```

3. **Install the required packages:**
   This command installs all dependencies and sets up the local `src` package in editable mode.
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the application:**
   ```bash
   python application.py
   ```
   Open your browser and navigate to `http://localhost:5000` to access the application.

## Deployment

The application is deployed on AWS (hosted on an AWS EC2 instance).

### System Architecture
- **WSGI Server:** Gunicorn serves the Flask web application ([application.py](file:///D:/Workspace/datascience-projects/math_marks_prediction/application.py)).
- **Reverse Proxy:** Nginx handles incoming HTTP traffic and proxies requests to the Gunicorn service on port 5000.
- **Service Management:** Managed as a systemd service to ensure continuous uptime and automatic recovery.
