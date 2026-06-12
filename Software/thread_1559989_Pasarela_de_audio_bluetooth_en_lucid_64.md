---
title: "Pasarela de audio bluetooth en lucid 64"
date: 2010-08-24
forum: Software
---

### Post by asterix77 on 2010-08-24
¿Alguien sabe  si es que los servicios (o perfiles ) de un bluetooh pueden estar  "escondidos" y por lo tanto no se pueden descubrir?

Quiero usar mi pc con lucid para escuchar los mp3 que contiene mi  celular usando bluetooth. Para ello debo crear una pasarela de audio en  mi pc.

#hcitool scan   Me arroja la mac de mi celular y su nombre, es decir lo detecta
 
Pero al hacer un browse con sdptool (para descubrir los servicios), aparece la mac más puntos ...... ej.

#sdptool scan
Scanning.......
XX:XX:XX:XX:XX:XX ......
# 

No sucede lo mismo con otros dispositivos, donde si descubre los servicios.

He instalado blueman, pero este solo me ha servido para enviar archivos al desde y hacia el celular.

¿Existe algún comando para obligar a descubrir los servicios que ofrece un bluetooth?

Saludos

---

