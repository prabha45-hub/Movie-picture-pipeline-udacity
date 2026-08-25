FROM python:3.10-slim-bookworm

ENV FLASK_RUN_HOST=0.0.0.0

WORKDIR /

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    build-essential \
    libpcre3-dev \
    libffi-dev \
    libssl-dev && \
    rm -rf /var/lib/apt/lists/* && \
    pip install --no-cache-dir pipenv

RUN useradd -u 1000 -m app

RUN mkdir -p /var/www/app /app

COPY Pipfile* /app/

RUN cd /app && pipenv install --system --deploy

COPY . /app

WORKDIR /app

CMD ["pipenv", "run", "serve"]
