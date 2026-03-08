# Multi-Lingual Learning Platform (MLP)

A comprehensive, multi-grade multilingual online learning platform supporting Grades 3-12. This repository contains the Python backend, designed to provide robust APIs, authentication, and data management for the platform.

## Table of Contents
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [API Documentation](#api-documentation)
- [Development Guidelines](#development-guidelines)
- [CI/CD Pipeline](#cicd-pipeline)
- [Contributing](#contributing)
- [Support](#support)

## Features

- **Comprehension Module**: Grade and language selection, topic browsing, assessments, progress tracking, and analytics.
- **Idioms & Expressions Module**: Search with autocomplete, idiom details, multilingual translations, examples, favorites management, and admin controls.
- **Online Glossary**: Alphabetical and subject-based term browsing, multilingual support, keyword search, and favorites.
- **Topic Search**: Advanced search with filters, rich media support, mathematical formula rendering, multilingual content, and personalized recommendations.
- **ChatBot Integration**: Interactive AI-powered learning assistant (future phase).

## Tech Stack

- **Backend**: FastAPI, Python 3.9+, Pydantic, Alembic, Pytest
- **Database**: MariaDB
- **Authentication**: Keycloak (OAuth 2.0, JWT, RBAC)
- **Search**: Elasticsearch (advanced topic search and indexing)
- **DevOps**: Docker, Docker Compose, Azure DevOps (CI/CD)
- **Code Quality**: Linting (Pylint/Flake8), Type Checking (mypy), Code Formatting (Black)

## Project Structure

```
.
├── app/                  # FastAPI application
│   ├── api/             # API endpoints and routes
│   ├── models/          # Pydantic data models
│   ├── services/        # Business logic layer
│   ├── schemas/         # Request/response schemas
│   └── core/            # Configuration and core utilities
├── docs/                # Documentation, specifications, and architecture diagrams
├── tests/               # Unit, integration, and end-to-end tests
├── infrastructure/      # CI/CD pipelines, Keycloak configuration, database scripts
├── .env.example         # Environment variables template
├── Dockerfile           # Docker image configuration
├── docker-compose.yml   # Multi-container orchestration
├── requirements.txt     # Python dependencies
└── README.md            # This file
```

## Prerequisites

- **Python**: 3.9 or higher
- **Docker**: 20.10+ and Docker Compose 1.29+
- **Git**: Latest version
- **.env file**: Properly configured (see [Getting Started](#getting-started))

Ensure all services (MariaDB, Keycloak, Elasticsearch) are accessible before running the application.

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/revathyrajabathar-dev/TestMCP.git
cd TestMCP
```

### 2. Configure Environment Variables

```bash
cp .env.example .env
```

Edit `.env` with your configuration values:
- Database credentials
- Keycloak server URL and credentials
- API keys and secrets
- Elasticsearch connection details

### 3. Start Development Environment

Using Docker:

```bash
docker build -t mlp-backend:latest .
docker run -d --name mlp-be-api -p 8000:8000 --env-file .env mlp-backend:latest
```

Or using Docker Compose (recommended):

```bash
docker-compose up -d
```

**Access the application:**
- **Backend API**: http://localhost:8000/api/v1/
- **Interactive API Docs**: http://localhost:8000/docs
- **Alternative API Docs**: http://localhost:8000/redoc

### 4. Run Tests

Execute the test suite to verify the setup:

```bash
# Run all tests
pytest

# Run with coverage report
pytest --cov=app

# Run specific test category
pytest tests/unit/
pytest tests/integration/
```

## API Documentation

Comprehensive API documentation is automatically generated and available at:
- **Swagger UI**: http://localhost:8000/docs
- **ReDoc**: http://localhost:8000/redoc

For detailed API specifications and endpoints, refer to the [/docs](./docs) directory.

## Development Guidelines

### Code Standards
- Follow **PEP 8** style guidelines for Python code.
- Use **type hints** for all function parameters and return types.
- Write clear, descriptive comments for complex logic.
- Keep functions small and focused (single responsibility principle).

### Version Control
- Use **Git Flow** branching strategy: `feature/`, `hotfix/`, `release/` branches.
- Write clear, descriptive commit messages following the [Conventional Commits](https://www.conventionalcommits.org/) standard.
- Create feature branches from `develop`, not `main`.

### Testing & Quality Assurance
- Write unit tests for business logic and services.
- Aim for **80%+ code coverage** for critical paths.
- Ensure code passes linting, formatting, and type checking before pushing:
  ```bash
  black app/                    # Code formatting
  pylint app/                   # Linting
  mypy app/                     # Type checking
  pytest --cov=app             # Testing with coverage
  ```
- Request code reviews and address feedback before merging PRs.

### Documentation
- Update or create documentation for new features, API endpoints, and modules.
- Use docstrings (Google or NumPy format) for all public functions and classes.
- Maintain API specifications in the `/docs` directory.

### Internationalization (i18n)
- All user-facing text and API responses must support multilingual content.
- Use i18n translation files for all localized strings.
- Test with multiple language packs before deployment.

## CI/CD Pipeline

Automated pipelines are configured using **Azure DevOps** with the following stages:

- **Build**: Compile and validate code
- **Test**: Execute unit and integration tests with coverage reporting
- **Lint & Quality**: Run code quality checks (Pylint, Flake8, mypy)
- **Security Scan**: Dependency and vulnerability scanning
- **Deploy**: Automated deployment to staging and production environments

Pipeline configuration: See `.azure-pipelines/` directory.

## Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature-name`)
3. Commit your changes following [Conventional Commits](https://www.conventionalcommits.org/)
4. Push to your fork (`git push origin feature/your-feature-name`)
5. Open a Pull Request with a clear description of your changes
6. Ensure all automated checks pass and address review comments

For more information, see [CONTRIBUTING.md](./CONTRIBUTING.md) (if available).

## Support

For questions, issues, or support, please:

- Check existing [Issues](https://github.com/revathyrajabathar-dev/TestMCP/issues)
- Review [Documentation](./docs)
- Contact the project maintainers or open a new issue

---

**License**: [Specify your license here]  
**Version**: 1.0.0  
**Last Updated**: March 2026