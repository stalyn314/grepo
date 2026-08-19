# Mi geoportal

Geoportal básico hecho con Leaflet. Incluye:
- Mapa base (OpenStreetMap)
- Capa de datos cargada desde `datos.geojson`
- Filtro por categoría (dropdown)
- Captura de puntos con clic
- Exportar puntos capturados a CSV

## Cómo publicarlo en GitHub Pages (gratis)

1. Crea una cuenta en https://github.com si no tienes.
2. Crea un repositorio nuevo:
   - Botón verde "New repository"
   - Nombre, por ejemplo: `geoportal`
   - Marca la opción "Public"
   - Click en "Create repository"
3. Sube estos 2 archivos al repositorio (`index.html` y `datos.geojson`):
   - Click en "Add file" > "Upload files"
   - Arrastra los archivos
   - Click en "Commit changes"
4. Activa GitHub Pages:
   - Ve a la pestaña "Settings" del repositorio
   - En el menú lateral click en "Pages"
   - En "Branch" selecciona `main` y carpeta `/root`
   - Click en "Save"
5. Espera 1-2 minutos. GitHub te dará un link tipo:
   `https://tuusuario.github.io/geoportal/`

Ese link ya lo puedes compartir o ponerlo en tu página de Wix (como botón con link,
o incrustado con un iframe).

## Cómo editar los datos

Abre `datos.geojson` y modifica los `features`. Cada punto necesita:

```json
{
  "type": "Feature",
  "properties": { "nombre": "...", "tipo": "...", "descripcion": "..." },
  "geometry": { "type": "Point", "coordinates": [LONGITUD, LATITUD] }
}
```

Importante: en GeoJSON el orden es [longitud, latitud] (al revés de lo normal).

El filtro del dropdown se llena automáticamente según los valores que uses en
el campo `"tipo"` de cada punto — no hay que tocar el código, solo el archivo
`datos.geojson`.

## Cómo probarlo en tu computadora antes de subirlo

No puedes abrir `index.html` con doble clic porque el navegador bloquea la
carga del archivo `datos.geojson` por seguridad (CORS). Para probarlo local:

1. Abre una terminal en la carpeta del proyecto
2. Ejecuta: `python3 -m http.server 8000`
3. Abre en el navegador: `http://localhost:8000`

En GitHub Pages esto no es un problema, funciona directo.
