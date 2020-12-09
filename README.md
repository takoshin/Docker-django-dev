# Docker-django-dev

Python 3.9 Django 3.1 MYSQL 8.0 nginx 1.19.2


--インストール後の設定方法--

#プロジェクトの作成
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
$ docker-compose run python django-admin.py startproject app_name .
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#日本時間と日本語の設定

"./src/app_name/settings.py"
~~~~~~~~~~~~~~~~~~~~~~~~
LANGUAGE_CODE = 'ja'
TIME_ZONE = 'Asia/Tokyo'
~~~~~~~~~~~~~~~~~~~~~~~~

#MYSQLとの接続

"./src/app_name/settings.py"
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'db_name',
        'USER': 'user',
        'PASSWORD': 'password',
        'HOST': 'db',
        'PORT': '3306',
    }
}
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#migrationの実施
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
$ docker-compose run python ./manage.py makemigrations

$ docker-compose run python ./manage.py migrate
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#管理者の設定
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
$ docker-compose run python ./manage.py createsuperuser
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#実行の確認
~~~~~~~~~~~~~~~~~~~~~~
$ docker-compose up -d
~~~~~~~~~~~~~~~~~~~~~~

"ブラウザ"
~~~~~~~~~~~~~~
localhost:8000
~~~~~~~~~~~~~~

#CSSの適用

"./src/app_name/settings.py"
~~~~~~~~~~~~~~~~~~~~~~~
STATIC_ROOT = '/static'
~~~~~~~~~~~~~~~~~~~~~~~

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
$ docker-compose run python ./manage.py collectstatic
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#CSSの動作確認
~~~~~~~~~~~~~~~~~~~~~~
$ docker-compose up -d
~~~~~~~~~~~~~~~~~~~~~~
"ブラウザ"
~~~~~~~~~~~~~~~~~~~~
localhost:8000/admin
~~~~~~~~~~~~~~~~~~~~
