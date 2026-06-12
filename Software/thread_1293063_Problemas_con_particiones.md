---
title: "Problemas con particiones"
date: 2009-10-16
forum: Software
---

### Post by lexer98 on 2009-10-16
hola chicos bue el problema es que quiero sacarle 10 gb a las particion de linux y darcelo a una particion NTFS el problema es que no me deja darle el espacio que le saque al a de linux a la particion NTFS mire la imagen:confused::confused:

Desde ya muchas gracias ! 

[[IMG]http://thumbnails22.imagebam.com/5262/8b55dc52616877.gif[/IMG]](http://www.imagebam.com/image/8b55dc52616877)

---

### Post by staar on 2009-10-16
estás en un problema, porque el espacio de las particiones tiene que ser continuo. mi recomendación sería que primero muevas tu sda5 hacia la derecha, hasta que quede junto a sda6 (esto se va a tomar su tiempo, son varios gigas que mover), y después achiques la extendida sda2 (el borde celeste) hasta que sea del tamaño de sda5 y sda6 juntas (que no quede espacio libre adentro). una vez hecho esto, vas a poder disponer del restante espacio libre como desees...

saludos

---

### Post by lexer98 on 2009-10-16
listo gracias lo pude solucionar

---

### Post by guillermolisi on 2009-10-16
> **lexer98 said:**
> listo gracias lo pude solucionar
Podes contarnos como terminaste resolviendo este tema ?

---

### Post by lexer98 on 2009-10-16
de la manera mas noob borre todas las partiones de ubuntu y volvi a instalar el S.o

---

