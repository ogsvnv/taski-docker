FROM python:3.10-slim

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

WORKDIR /app

# Установка зависимостей
COPY requirements.txt .
RUN pip install --upgrade pip && pip install -r requirements.txt

# Копируем проект
COPY . .

# Собираем статику сразу при сборке контейнера
RUN python manage.py collectstatic --noinput

# Используем Gunicorn для продакшена
CMD ["gunicorn", "backend.wsgi:application", "--bind", "0.0.0.0:8000"]