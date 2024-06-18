# Django Allauth Login System

Este é um projeto Django que implementa um sistema de login usando `django-allauth`. O projeto permite que os usuários se registrem, façam login, redefinam suas senhas e verifiquem seus endereços de email.

## Requisitos

- Python 3.12
- Django 5.0.6
- `django-allauth`
- `python-dotenv`

## Instalação

### 1. Clonar o repositório

```bash
git clone https://github.com/seu-usuario/django-allauth-login.git
cd django-allauth-login


2. Criar e ativar o ambiente virtual

python -m venv venv
source venv/bin/activate  # No Windows, use `venv\Scripts\activate`

3. Instalar as dependências
pip install -r requirements.txt

4. Configurar as variáveis de ambiente

SECRET_KEY=yourprojectsecretkey
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USE_TLS=True
EMAIL_HOST_USER=email
EMAIL_HOST_PASSWORD=password

5. Migrar o banco de dados

python manage.py migrate

6. Criar um superusuário

python manage.py createsuperuser

7. Executar o servidor de desenvolvimento

python manage.py runserver

Configuração do Projeto

settings.py

Certifique-se de que as configurações no seu settings.py estejam corretas:

import os
from dotenv import load_dotenv

load_dotenv()

EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
EMAIL_HOST = os.getenv('EMAIL_HOST')
EMAIL_PORT = int(os.getenv('EMAIL_PORT', 587))
EMAIL_USE_TLS = os.getenv('EMAIL_USE_TLS') == 'True'
EMAIL_HOST_USER = os.getenv('EMAIL_HOST_USER')
EMAIL_HOST_PASSWORD = os.getenv('EMAIL_HOST_PASSWORD')

INSTALLED_APPS = [
    ...
    'django.contrib.sites',
    'allauth',
    'allauth.account',
    'allauth.socialaccount',
    ...
]

AUTHENTICATION_BACKENDS = [
    ...
    'django.contrib.auth.backends.ModelBackend',
    'allauth.account.auth_backends.AuthenticationBackend',
    ...
]

SITE_ID = 1

ACCOUNT_EMAIL_VERIFICATION = 'mandatory'
ACCOUNT_EMAIL_REQUIRED = True
ACCOUNT_AUTHENTICATION_METHOD = 'email'
ACCOUNT_UNIQUE_EMAIL = True


urls.py
Adicione as URLs do django-allauth ao seu urls.py:

from django.urls import path, include

urlpatterns = [
    ...
    path('accounts/', include('allauth.urls')),
    ...
]

Funcionalidades
Registro de usuários com verificação de email
Login e logout de usuários
Redefinição de senha via email
Edição do perfil do usuário

Contribuição
Sinta-se à vontade para abrir issues e enviar pull requests. Toda contribuição é bem-vinda!
