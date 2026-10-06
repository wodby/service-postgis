# PostgreSQL (PostGIS) on Wodby

What this service adds to the PostgreSQL service it is based on.

- The image bundles PostGIS, and `POSTGRES_DB_EXTENSIONS` has a default: `postgis`, `postgis_raster`, `postgis_sfcgal`, `fuzzystrmatch`, `address_standardizer`, `address_standardizer_data_us`, `postgis_tiger_geocoder` and `postgis_topology`. These extensions are created in a database when Wodby creates it; the application does not run `CREATE EXTENSION postgis`.
- Setting `POSTGRES_DB_EXTENSIONS` on this service replaces the whole default list. To add an extension such as `vector`, repeat the PostGIS extensions that are needed and append it.

Everything else, including the database, user, ownership, configuration, backups and imports, is as in the PostgreSQL service.

## Check the result

In the database container, `PGPASSWORD="$POSTGRES_PASSWORD" psql -h localhost -U postgres -d <database> -c 'SELECT postgis_full_version();'` shows the PostGIS version in a database.
