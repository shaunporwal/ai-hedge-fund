FROM python:3.11-slim

WORKDIR /app

# Set PYTHONPATH to include the app directory
ENV PYTHONPATH=/app

# Install uv
RUN pip install uv

# Copy only dependency files first for better caching
COPY ../pyproject.toml /app/

# Install dependencies with uv
RUN uv sync --no-dev

# Copy rest of the source code
COPY ../ /app/

# Default command (will be overridden by Docker Compose)
CMD ["uv", "run", "python", "src/main.py"] 
