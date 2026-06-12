---
title: "Problemas al momento de abrir Equipo"
date: 2009-07-20
forum: Software
---

### Post by DiegoTc on 2009-07-20
Cada vez que deseo abrir Equipo
Se me cierra automaticamente, se me cierra todos las carpetas que tengo abiertas, y de paso todos los iconos del escritorio desaparecen. No tengo la menor idea a que se deba esto :(

---

### Post by staar on 2009-07-20
por alguna razón, nautilus se está cerrando...

hacé una cosa, cuando se cierre, abrí una terminal y corré, primero, y por las dudas ```
killall nautilus
``` y después ```
nautilus
``` esperá que termine de abrir e intentá abrir Equipo de nuevo, el error que te salga en la terminal pegalo acá...

saludos

---

### Post by DiegoTc on 2009-07-22
Bueno perdon por la tardanza.
Aqui esta 

> 
diego@diego-laptop:~$ nautilus

** (nautilus:5418): WARNING **: Unable to add monitor: No soportado
Fallo de segmentación



Se me abre la carpeta home.Y cuando le doy click a Equipo de me cierra y en terminal me aparece Fallo de segmentacion

---

### Post by staar on 2009-07-22
de casualidad tenés instalado ubuntu one? porque hay un bug reportado muy similar acá [https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/395710]("https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/395710") en teoría actualizando el cliente de ubuntu one se debería resolver...

saludos

---

