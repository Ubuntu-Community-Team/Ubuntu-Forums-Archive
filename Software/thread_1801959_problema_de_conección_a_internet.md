---
title: "problema de conección a internet"
date: 2011-07-11
forum: Software
---

### Post by atonau on 2011-07-11
Amigos:

Tube que reinstalar todo... despues del formateo correspondiente.... estaba más lento que el acuerdo entre el mineduc y los alumnos... pero ahora el 11.04, que ya tenía de antes, no se conecta a internet... tengo red cableada con telefónica chile.... ¿que puedo hacer?

---

### Post by silex89 on 2011-07-22
Tu red es DHCP? o PPPoE? hace tiempo tenía exactamente el mismo problema, y resultó ser un problema de DNS (yo tenía una conexión PPPoE), se resolvió con una llamada a la empresa y rectificaron todo :D


Suerte :)

---

### Post by papibe on 2011-07-22
Server o Escritorio?

Puedes publicar el resultado de los siguientes comandos?
```
$ ifconfig

$ route -n

$ nslookup google.com
```
Saludos.

---

