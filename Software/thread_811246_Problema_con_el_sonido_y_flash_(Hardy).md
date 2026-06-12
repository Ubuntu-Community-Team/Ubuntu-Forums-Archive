---
title: "Problema con el sonido y flash (Hardy)"
date: 2008-05-28
forum: Software
---

### Post by nemodot on 2008-05-28
Buenas, desde que actualicé a Hardy que tengo este terrible problema. Sucede que no puedo escuchar musica del amarok o de cualquier otro reproductor de musica si al mismo tiempo tengo alguna ventana del firefox con algun contenido en flash, especialmente youtube. Y lo más grave es que el amarok se cuelga cuando quiero poner a reproducir algún tema en estas condiciones.

Otro de mis problemas con el sonido, y lo tengo desde que por primera vez instale ubuntu es que en general es muy bajo y tengo que subirlo demasiado para escucharlo decentemente, después cuando mi hermano va a windows, me parten los oídos la musiquita de windows xp con los parlantes al mango que tengo desde mi ultima sesión en ubuntu. 

Alguien ha experimentado alguno de estos problemas?

---

### Post by atatiducken on 2008-05-29
por lo del sonido bajo proba tipeando **alsamixer** en una terminal y pone los volumenes al palo, con ESC  salis y queda guardado.
Por lo del sonido no se bien, proba instalando el paquete **libflashsupport** y reinicia y fijate si se soluciono, saludos

---

### Post by sajnox on 2008-05-29
Yo tambien tuvo algunos temas con el sonido y con hardy, para solucionarlo anda a las opciones de Sonido 

/sistema/preferencias/sonido

Ahi tenes varias opciones de configuracion del server de sonido (Alsa, Oss, Pulseaudio, etc) y un boton para probar que suene. Elegi el que suena y eso lo tenes que repetir tambien en amarok en settings/engine.

Por el lado del volumen bajo comentanos que placa de audio tenes, yo en la notebook tuve que corregir un archivo de configuracion y levanto el volumen considerablemente.

Saludos

---

