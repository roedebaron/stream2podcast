FROM python:3.10.6-slim-buster AS runtime


WORKDIR /app

RUN pip install --upgrade pip

# Install poetry
RUN pip install poetry

# Copy only requirements to cache in docker layer
COPY pyproject.toml poetry.lock /app/

# Install packages, do not create virtualenv in docker
RUN poetry config virtualenvs.create false
RUN poetry install --no-dev

COPY ./main.py .
COPY ./src ./src

RUN ls

ENTRYPOINT poetry run python main.py

