---
title: "Grub lento karmic koala"
date: 2009-11-03
forum: Software
---

### Post by lucasgz on 2009-11-03
instale el ubuntu 9.10 desde cero y tarda mucho mas en cargar el grub que cuando tenia el 9.04, ahora se queda 10 seg en pantalla negra con "GRUB Loading."
 ademas el grub q me instalo es 1.97 beta 4 y por ahi decian que venia con el grub2
saben porque puede ser?

la pc : micro AMD athlon dual core 2,2 GHz
          1GB ram
          placa de video 8400 gs

---

### Post by oktubrer on 2009-11-05
Respecto a la versión, es correcta la que mencionas, 1.97 beta.
Por tu error, hay un bug en launchpad reportado por lo mismo (en ingles):

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)

Según estuve leyendo, el problema es cuando tienen el grub2 instalado en un disco distinto a donde esta el /boot

---

### Post by lucasgz on 2009-11-07
tengo en un disco todo windows y en otro disco el ubuntu, particionado en /home y el resto, sera por eso?
bueno de todas maneras es cuestion de esperar una actualizancion del grub, gracias por la info :)

---

