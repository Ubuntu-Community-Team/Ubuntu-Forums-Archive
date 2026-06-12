---
title: "¿Cómo asociar chromium a libreoffice y lectores de pdf?"
date: 2012-02-02
forum: Software
---

### Post by donmatas on 2012-02-02
Hola:

tengo chromium como mi navegador predeterminado en mi Ubuntu 10.04 (como pueden ver en el pantallazo adjunto)
Mi problema es que cuando pincho un hipervínculo en un documento que no esté en chromium (vg. libreoffice, evince o calibre) invariablmente lo abre con firfox (¡cuec!) ¿cómo puedo arreglar eso?

gracias
DM

---

### Post by juancarlospaco on 2012-02-02
xdg-mime query default mimetype
xdg-mime default application.desktop mimetype

Ej:
xdg-mime query default pdf
xdg-mime default programa.desktop pdf

El programa modifica automaticamente el archivo de texto plano de configuracion en el /home .

Creo que sacando un paquete llamado ubufox tambien se deshace ese comportamiento.

---

### Post by donmatas on 2012-02-02
> **juancarlospaco said:**
> xdg-mime query default mimetype
xdg-mime default application.desktop mimetype

Ej:
xdg-mime query default pdf
xdg-mime default programa.desktop pdf

El programa modifica automaticamente el archivo de texto plano de configuracion en el /home .

Creo que sacando un paquete llamado ubufox tambien se deshace ese comportamiento.

gracias juancarlospaco.
Para serte sincero no me queda claro que lo tengo que hacer

saludos
DM

---

### Post by juancarlospaco on 2012-02-02
jejeje..., esta bien, vamos despacio, 
busca en el centro de software un paquete llamado ubufox y desinstalalo,
es posible que lo solucione; sino vemos otra manera...

:)

---

### Post by donmatas on 2012-02-03
gracias compa por la diligencia!
Desinstalé vía CSU el paquete ubufox y xul-ext-ubufox, reinicié y luego abrí un link de un .odt y se abrió firefox :(

¿qué hago ahora?

salud
DM

---

### Post by juancarlospaco on 2012-02-03
Tenes LibreOffice o OpenOffice instalado?, funcionan?
El Chromium desde donde lo instalaste?, como hiciste?

Todas las asociaciones a tipos de archivos (mime-type) estan en 1 archivo de texto:

Lado de Sistema (SystemWide, para todos los usuarios):
cat /usr/share/applications/defaults.list

Lado de Usuario (UserLand, para 1 usuario solamente):
cat $HOME/.local/share/applications/defaults.list

Si por las buenas no se comporta como deseamos,
hay que editar ese archivo (previo backup claro),
viendo el archivo enseguida te das cuenta la sintaxis:

tipo/subtipo=programaQueLoAbre.desktop
ej:  
video/webm=totem.desktop

---

### Post by donmatas on 2012-02-03
> **juancarlospaco said:**
> Tenes LibreOffice o OpenOffice instalado?, funcionan?
El Chromium desde donde lo instalaste?, como hiciste?

Todas las asociaciones a tipos de archivos (mime-type) estan en 1 archivo de texto:

Lado de Sistema (SystemWide, para todos los usuarios):
cat /usr/share/applications/defaults.list

Lado de Usuario (UserLand, para 1 usuario solamente):
cat $HOME/.local/share/applications/defaults.list

Si por las buenas no se comporta como deseamos,
hay que editar ese archivo (previo backup claro),
viendo el archivo enseguida te das cuenta la sintaxis:

tipo/subtipo=programaQueLoAbre.desktop
ej:  
video/webm=totem.desktop

Mil gracias compa!
Sí, tengo instalado libreoffice (removí ooffice apenas se lo apropió Oracle) y funciona de maravillas. Chromuim lo instalé desde el CSU (o quizás de la terminal), pero definitivamente de los repositorios oficiales según recuerdo.

Te cuento lo que hice. 
Primero:
```
sudo gedit /usr/share/applications/defaults.list

```

luego respaldé el archivo y busqué [ctrl+f] las líneas en que aparecía firefox  y mozilla con los siguientes resultados:
mozilla: sin resultados
firefox: 
```
text/xml=firefox.desktop
text/html=firefox.desktop;calibre-gui.desktop;calibre-ebook-viewer.desktop
application/xhtml+xml=firefox.desktop;calibre-gui.desktop;calibre-ebook-viewer.desktop

```

luego procedí a cambiarlo así:

```
text/xml=**chromium-browser**.desktop
text/html=**chromium-browser**.desktop;calibre-gui.desktop;calibre-ebook-viewer.desktop
application/xhtml+xml=**chromium-browser**.desktop;calibre-gui.desktop;calibre-ebook-viewer.desktop
```

Lo probé y no funciona. Sigue usando Firefox para abrir los hipervínculos. 

Luego reinicié y el problema persiste.
:(

¿alguna sugerencia?
salud
DM

---

### Post by juancarlospaco on 2012-02-03
gconf-editor

CTRL + F

firefox

proba reemplazar por chromium 
*(1 por 1, despues logout/login y proba)*

Es muy raro lo que esta pasando, chequeaste el que esta en $HOME ?

---

### Post by donmatas on 2012-02-03
> **juancarlospaco said:**
> gconf-editor

CTRL + F

firefox

proba reemplazar por chromium 
*(1 por 1, despues logout/login y proba)*

Es muy raro lo que esta pasando, chequeaste el que esta en $HOME ?

En G-conf dice "patrón no encontrado" (adjunto pantallazo)
En cuanto a la ruta en /home, el fichero no existe (idem)

salud
DM

---

### Post by juancarlospaco on 2012-02-03
Crealo,
con los parametros correctos...

(lo necesitas al Firefox?, si lo desinstalas no pasa nada, y seguro anda)

---

### Post by donmatas on 2012-02-20
gracias JC
¿cuáles son los parámetros correctos?

Prefiero no desinstalar firefox, pues aveces se necesita

saludos
DM

---

