# Consultor PLM · Farmacias San Camilo

Asistente web de consulta de medicamentos basado en la base PLM, pensado para uso operativo en farmacia.

## Estado del proyecto

- Frontend estático (GitHub Pages)
- Sin backend y sin dependencia obligatoria de LLM para responder
- Respuestas determinísticas con datos locales
- Soporte de desambiguación y modo de respuesta rápida/completa

## Funcionalidades principales

- Consulta por nombre de producto y términos clínicos
- Secciones de ficha técnica:
  - composición
  - indicaciones
  - contraindicaciones
  - embarazo/lactancia
  - interacciones
- Comparaciones (`A vs B`)
- Similares por sustancia activa
- Listados por sustancia (tabla)
- Desambiguación cuando hay múltiples coincidencias
- Modo de respuesta:
  - `Rápida` (operación mostrador)
  - `Completa` (detalle técnico)

## Estructura de datos usada en runtime

- `index.html` -> aplicación principal
- `plm_data.json` -> base principal de productos
- `indice_rutas_plm.json` -> mapeo URL PLM -> archivo markdown
- `secciones/` -> fichas estructuradas por producto
- `indice_imagenes_producto.json` -> índice preferente de imágenes
- `indice_imagenes_plm.json` -> índice de respaldo de imágenes
- `logo_asistente.ico`, `logo_asistente.jpg`, `logo_san camilo.png` -> branding

## Ejecución local

Desde la carpeta del proyecto:

```bash
python -m http.server 5500
```

Abrir en navegador:

`http://localhost:5500`

## Publicación en GitHub Pages

1. Subir rama `main` al repositorio.
2. Ir a `Settings > Pages`.
3. Seleccionar `Deploy from a branch`.
4. Branch: `main`, carpeta: `/ (root)`.
5. Guardar y esperar el despliegue.

## Archivos que NO conviene subir

- `indice_conocimiento_plm.json` (excede límite de GitHub)
- `BASE_CONOCIMIENTO_PLM_COMPLETA.md` (muy pesado)
- `~$*.xlsx` (temporales de Excel)
- `__pycache__/`

## Índice de imágenes (opcional)

Para regenerar el índice de imágenes por producto desde origen PLM:

```bash
python build_indice_imagenes_producto.py --max 800 --delay 0.2
```

Puedes ejecutarlo por lotes; el JSON resultante se actualiza de forma incremental.

## Aviso legal

Este sistema entrega información de referencia y no sustituye criterio médico profesional.
Verificar siempre normativas sanitarias locales y lineamientos institucionales vigentes.
