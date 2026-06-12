---
title: "Problemas molestos dns y otros..."
date: 2008-08-24
forum: Software
---

### Post by pol666 on 2008-08-24
Hola gente, estoy con un ubuntu recien instalado, Tengo un pqueño problema, cuando reinicio la computadora la lista de dns que esta en el resolv.conf se borra por lo que tengo que volver a poner los servidores dns sino no puedo navegar. Eso me imagino que tengo que poner los dns en el router para no volver a ponerlos... no se como se hace pero despues me fijo.

Otro problema molesto es que no inicia conectada, tengo que hacer click en el applet de red y activar "red cableada" antes eso no pasaba :\

Por ultimo esto nada que ver pero capas que saben: Estoy usando reiserfs, puede ser que tarde mas en iniciar el sistema por ese tipo de particiones, lo noto un poco lento el arranque...pues


Saludos

---

### Post by leo_rockway on 2008-08-26
Con respecto a los DNS fijate de hacer esto:

En el archivo /etc/dhcp3/dhclient.conf busca la parte donde dice "prepend domain-name-servers", descomentala y cambiale el 127.0.0.1 por tus direcciones DNS.

O como vos dijiste, se puede configurar directamente desde el router (al menos en el mio se puede).

---

### Post by fmsismo on 2008-08-26
No creo que sea por el sistema de archivos.  Yo use reiserfs mucho tiempo y no tuve ningun problema.  A nivel de performance es más o tan bueno como ext3.  No tendrás algún servicio que necesite de internet y espera hasta el timeout cuando inicia (onda el ntpdate)?

Saludos

---

