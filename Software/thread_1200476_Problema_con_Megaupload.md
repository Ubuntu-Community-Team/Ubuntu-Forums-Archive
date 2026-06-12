---
title: "Problema con Megaupload"
date: 2009-06-30
forum: Software
---

### Post by Tosh78 on 2009-06-30
A alguno le paso que no le funiona Megaupload?
Desde ayer que cada vez que clickeo en un link de Megaupload el Firefox se queda tildado pensando. Lo probe tambien con el Opera y me pasa lo mismo. Sin embargo, probe en iniciar con win en la misma maquina y probar con Firefox y funciona, con lo cual descarto que sea algo de la conexion. 
Me pueden dar una mano o explicar por que puede pasar esto?

---

### Post by Hei Ku on 2009-06-30
Tenés Telefónica? Fijate acá: [http://ubuntuforums.org/showpost.php?p=7537342&postcount=45](http://ubuntuforums.org/showpost.php?p=7537342&postcount=45)

---

### Post by Mister X on 2009-06-30
si, a mi me viene pasando desde el sabado, con espidi

sin embargo hace un ping:
```

ping megaupload.com
PING megaupload.com (69.5.88.231) 56(84) bytes of data.
64 bytes from hosted.by.cirn.net (69.5.88.231): icmp_seq=1 ttl=51 time=232 ms

```

y accede directamente por IP: [http://69.5.88.231](http://69.5.88.231) :p

si tenes un link para descargar, hace lo mismo, reemplaza el dominio por la IP

---

### Post by Hei Ku on 2009-06-30
Y quejense con su ISP por el mal servicio.

---

### Post by josecuervo86 on 2009-06-30
Con el atajo de poner "1" despues de www anda bien! ejemplo del caso: ```
www1.megaupload.com
```
Es lo mismo que hago aca en el foro, porque tambien anda mal. Por suerte no soy el único con el mismo problema.

---

### Post by Tosh78 on 2009-06-30
Hola a todos!
Muchas gracias por las respuestas. Voy a probar lo de la ip y lo del www1.
No tengo Telefonica Hei Ku, ya que no vivo en Argentina. Voy a probar con esos consejos que me dieron y si me lo estan filtrando me voy a quejar con el ISP.

---

### Post by Fistandantilus on 2009-07-01
Parece q enrealidad hay un problema con todos los dns por un bloqueo que viene desde francia a megaupload.
Yo lo pude solucionar tranquilamente modificando el hosts, le agregue las siguientes lineas:

69.5.88.212 megavideo.com
69.5.88.212 [www.megavideo.com]("http://www.megavideo.com/")
69.5.88.212 wwwstatic.megavideo.com
95.211.94.210 www881.megavideo.com

Saludos

---

