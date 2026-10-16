# English Studio · Generador de ejercicios de inglés

Aplicación gratuita y sin conexión. No necesita cuentas, claves de API ni instalar dependencias. Interfaz en español y ejercicios e instrucciones en inglés británico.

## Abrir y utilizar (sin conocimientos de programación)

1. Descarga el repositorio desde GitHub: botón **Code → Download ZIP**.
2. Descomprime el ZIP en una carpeta de tu ordenador.
3. Abre **index.html** con Chrome, Edge, Firefox o Safari. Conserva los archivos `bank.js`, `app.js` y `styles.css` en la misma carpeta.
4. Elige nivel, contenido, modalidad, cantidad y dificultad. Pulsa **Generar actividad**.
5. Escribe las respuestas y pulsa **Corregir respuestas**. En las modalidades abiertas escribe la oración completa; en huecos, solamente las palabras que faltan.
6. Pulsa **Mostrar soluciones** para consultar los modelos y las reglas gramaticales. **Borrar respuestas** permite volver a practicar la misma ficha.
7. Para otra selección aleatoria, pulsa de nuevo **Generar actividad**. Cambiar los selectores no modifica la ficha hasta que pulses ese botón.

## Imprimir o guardar en PDF

- **Imprimir ficha / PDF** crea una ficha sin respuestas ni correcciones, aunque hayas mostrado las soluciones en pantalla. Incluye nombre y fecha.
- **Imprimir soluciones** crea un documento independiente con las respuestas modelo y explicaciones.
- En el diálogo del navegador, elige papel **A4**. Desactiva los encabezados y pies del navegador para una presentación más limpia. Para descargar un PDF, selecciona **Guardar como PDF** como impresora/destino.
- Para imprimir los dos documentos, usa los dos botones por separado.

## Contenido y límites de la primera versión

El banco contiene **320 registros**, 20 por contenido, reutilizables en siete modalidades. Los contenidos disponibles dependen del nivel; cada actividad selecciona registros sin repetición. Al regenerar una ficha pueden volver a aparecer preguntas de fichas anteriores. Las actividades de 20 preguntas usan todos los registros del contenido, en orden aleatorio.

A1: presente simple y continuo, pasado simple, futuro con *going to*, capacidad con *can* y comparativos y superlativos. A2 añade pasado continuo, presente perfecto, futuro con *will* y consejos con *should*. B1 añade primer y segundo condicional, pasiva en pasado y relativas con *who*. B2 añade estilo indirecto. Los contenidos básicos siguen disponibles en niveles superiores para repaso. Las etiquetas PET y First indican el nivel de referencia: no son simulacros oficiales ni cubren todo su temario. Esta versión trabaja las formas indicadas en los títulos de cada contenido.

La dificultad ajusta el apoyo, no introduce contenidos de otro nivel: **Guiada** muestra regla y pista; **Estándar** muestra una pista breve; **Reto** elimina las ayudas. Las frases tienen vocabulario cotidiano controlado y estructuras repetibles para practicar una regla. Revisa la ficha antes de entregarla.

La corrección ignora mayúsculas, puntuación final y espacios extra, y admite contracciones negativas habituales. Las traducciones y preguntas usan modelos: una alternativa correcta puede no coincidir. La aplicación lo avisa y permite revisar el modelo con el profesor; no pretende evaluar automáticamente todas las paráfrasis. No analiza pronunciación ni utiliza IA.

Los datos solo viven en la pestaña: al recargar se pierden las respuestas y la actividad. Guarda una copia PDF si deseas conservarla. No hay analítica, cookies ni peticiones externas.

## Arquitectura

- `index.html`: interfaz y controles accesibles.
- `styles.css`: diseño adaptable y estilos de impresión A4.
- `bank.js`: datos léxicos y plantillas por nivel/contenido, respuestas, errores de contraste y explicaciones.
- `app.js`: proveedor local, selección aleatoria, modalidades, corrección y presentación.

Para ampliar el banco, añade registros o plantillas en `bank.js` conservando respuestas revisables. El contrato del proveedor local es `generate(settings) → records`; una integración posterior con IA puede sustituir este proveedor. Una futura integración requeriría un servidor para proteger las claves y validación pedagógica de los registros antes de mostrarlos. Esta versión no requiere dicho servidor.

## Desarrollo opcional

Trabaja en el checkout existente; no hace falta crear un worktree. No hay proceso de compilación ni gestor de paquetes.

Para servir la aplicación localmente en lugar de abrir el HTML:

```sh
cd /workspace/generador-ejercicios-ingles
python3 -m http.server 8000 --bind 0.0.0.0
```

Abre la dirección del servidor en tu propio ordenador cuando ejecutes allí el comando. En el entorno cloud, el servidor sirve para validación interna; no se necesita para usar el ZIP descargado.
