# Finanzas del Hogar — guía de instalación (paso a paso)

La app parte **vacía**. Usa el modelo de tu planilla: Ingresos, Gastos fijos (pagado + cuota), Gastos variables, Ahorros (banco y tipo) y Resumen mensual.
Con la nube activada, tus datos quedan **guardados en tu cuenta de correo**: si borras la app, cambias de celular o usas un computador, entras con tu correo y todo vuelve.

## PARTE 1 — Crear la nube (Firebase, gratis) — hazlo ANTES de publicar
1. Entra a **console.firebase.google.com** > **Agregar proyecto** > nombre `finanzas-hogar` > sin Google Analytics.
2. Menú izquierdo **Compilación > Authentication > Comenzar > Correo electrónico/contraseña > Habilitar > Guardar**.
3. **Compilación > Firestore Database > Crear base de datos** > ubicación `southamerica-east1` (São Paulo) > modo **producción**.
4. Pestaña **Reglas**: borra todo, pega el contenido de `firestore.rules`, cambia los dos correos por los de ustedes dos y pulsa **Publicar**.
5. Rueda ⚙ > **Configuración del proyecto** > baja a *Tus apps* > ícono **</>** (Web) > ponle un nombre > **Registrar app**. Copia los valores `apiKey`, `authDomain`, `projectId`, `appId`.
6. Abre el archivo **`firebase-config.js`** (Bloc de notas) y pega esos 4 valores entre las comillas. Guarda.
   (La apiKey de Firebase no es un secreto: la protección está en las reglas del paso 4.)
7. Authentication > pestaña **Settings > Dominios autorizados > Agregar dominio**: agrega `TU-USUARIO.github.io` (el de la Parte 2).

## PARTE 2 — Publicar la app (GitHub Pages, gratis)
1. github.com > **New repository** > `finanzas-hogar` > Create. (Sólo contiene código, nunca tus datos.)
2. **Add file > Upload files**: sube TODO el contenido de esta carpeta (incluido `firebase-config.js` ya editado) > **Commit changes**.
3. **Settings > Pages > Branch: main / (root) > Save**.
4. En 1–2 minutos queda en `https://TU-USUARIO.github.io/finanzas-hogar/`. Esa dirección sirve en celular y computador.

## PARTE 3 — Primer ingreso (cada persona)
1. Abre la dirección > **Crear cuenta** con tu correo (el mismo que pusiste en las reglas) y una contraseña.
2. Llega un correo de Firebase: abre el enlace para **verificar**. Vuelve a la app y pulsa **Entrar**.
3. Ahí mismo la app te ofrece crear una **contraseña de bloqueo** para este dispositivo. En Ajustes > Seguridad activa **rostro / huella**.
4. Instala la app: **iPhone (Safari):** Compartir > *Añadir a pantalla de inicio*. **Android (Chrome):** menú ⋮ > *Instalar app*.
5. La segunda persona hace lo mismo con su correo. Ven los mismos datos.

## Si cambias de celular, borras la app o usas un computador
Abre la misma dirección > **Entrar** con tu correo y contraseña. Tus datos se descargan solos. ¿Olvidaste la contraseña? Botón **Olvidé mi contraseña**.

## Excel / Google Drive
- Ajustes > **Exportar Excel**: una hoja por mes con tu disposición + RESUMEN con fórmulas. Súbelo a Drive como respaldo extra.
- **Importar Excel** y **Respaldo JSON** también disponibles.

## Cierre mensual
Inicio > **Cerrar mes**: bloquea el mes y abre el siguiente con tus ingresos, gastos fijos, ahorros y cuotas (3/12 → 4/12).

## ¿Es seguro?
- Los datos van a TU proyecto de Firebase por HTTPS y Google los cifra en reposo. Sólo entran los 2 correos de las reglas, con correo verificado.
- No es cifrado de extremo a extremo: quien administre el proyecto de Firebase podría verlos. Usa una contraseña larga y distinta a la de otros sitios.
- La clave/rostro de la app bloquea el acceso en ese dispositivo; mantén también el bloqueo de pantalla del teléfono.
- Funciona sin internet y sincroniza al volver. Si ambos editan el MISMO mes sin conexión, gana el último en guardar.
- Hecho para 2 personas; si agregas más correos, edita las reglas.
