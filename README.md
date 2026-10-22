# Gestión de Proyectos y Tareas

## Objetivo

Aplicación web para administrar proyectos y las tareas asociadas a cada uno, usando el administrador de Django.

## Tecnologías

- Python 3.14
- Django 6.1.2
- SQLite, almacenado en `db.sqlite3` en la raíz del proyecto

## Modelos y relación

- `Proyecto` (`gestion/models.py`): guarda `nombre`, `descripcion` y `fecha_inicio`.
- `Tarea` (`gestion/models.py`): guarda `titulo`, `completada` y una referencia `proyecto`.
- Cada tarea pertenece a un proyecto mediante una clave foránea (`ForeignKey`) con el nombre inverso `tareas`. Si se elimina un proyecto, Django elimina sus tareas asociadas (`on_delete=models.CASCADE`).

## Migraciones y administración

Las migraciones de la aplicación están en `gestion/migrations/`. `0001_initial.py` crea los modelos `Proyecto` y `Tarea`. Los dos modelos están registrados en `gestion/admin.py`; el panel está disponible en `/admin/`.

## Preparar y ejecutar en Windows PowerShell

Desde la raíz del proyecto (`Parcial2_Django`):

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

Abre `http://127.0.0.1:8000/`. Para el administrador, visita `http://127.0.0.1:8000/admin/` e inicia sesión con un usuario administrador existente. Si no tienes uno, créalo con `python manage.py createsuperuser`.

La configuración local usa `db.sqlite3`; no la elimines ni la reemplaces si quieres conservar sus registros. La clave Django se carga desde `DJANGO_SECRET_KEY` o se genera y guarda localmente en `.django_secret`, archivo excluido de Git. `DJANGO_DEBUG` está desactivado por defecto y los hosts locales permitidos son `localhost` y `127.0.0.1`.

Las dependencias están fijadas en `requirements.txt`.
