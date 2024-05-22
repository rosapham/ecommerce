# Local setup environment

Run "pip-compile --output-file=requirements/prod.txt pyproject.toml" to create package dependencies for the project
Run "pip-compile --extra test -o requirements/test.txt pyproject.toml" to create package dependencies for the testing
Run "pip-compile --extra dev -o requirements/dev.txt pyproject.toml" to create package dependencies for the development

# Install requirements files

Run "pip install -r requirements/prod.txt ."
When developing run "pip install -r requirements/dev.txt ."
When testing run "pip install -r requirements/test.txt ."

# Setup Database Migration

Run "alembic init -t async migrations"
Change sqlalchemy.url to the postgres database
Change value for target_metadata with "SQLModel.metadata" in env.py file
Import all models into env.py and init.py file (in folder models)
Import sqlmodel into the script.py.mako file
Run: alembic revision --autogenerate -m "Added new table"
Run: "alembic upgrade head" (or the revision id) to upgrade the database
Run: "alembic downgrade -1" (or the revision id) to downgrade the datase
