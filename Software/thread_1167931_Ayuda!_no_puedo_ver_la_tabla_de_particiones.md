---
title: "Ayuda! no puedo ver la tabla de particiones"
date: 2009-05-23
forum: Software
---

### Post by leosr on 2009-05-23
Hola.
Estuve bajando, para probar, live Cds de distintas distribuciones. Entre ellas el disco 1 de Debian 5 Lenny. Sucede que no es un live CD, y me metí en la instalción gráfica, que al darme cuenta la aborté. Volví a iniciar mi Ubuntu Intrepid sin problemas, salvo que cuando quiero instalar Jaunty no me reconoce las particiones del disco, me pide particionar el disco cosa que no puedo hacer porque me borra todo el contenido, incluso probé desde el live Cd con GParted y me dice que está "sin asignar". Cómo restauro la información de la tabla de particiones???
Empezé con Hardy, todavia me considero novato.
Espero que me puedan ayudar, no quiero borrar todo el HD.

Saludos.

---

### Post by guillermolisi on 2009-05-23
> **leosr said:**
> Hola.
Estuve bajando, para probar, live Cds de distintas distribuciones. Entre ellas el disco 1 de Debian 5 Lenny. Sucede que no es un live CD, y me metí en la instalción gráfica, que al darme cuenta la aborté. Volví a iniciar mi Ubuntu Intrepid sin problemas, salvo que cuando quiero instalar Jaunty no me reconoce las particiones del disco, me pide particionar el disco cosa que no puedo hacer porque me borra todo el contenido, incluso probé desde el live Cd con GParted y me dice que está "sin asignar". Cómo restauro la información de la tabla de particiones???
Empezé con Hardy, todavia me considero novato.
Espero que me puedan ayudar, no quiero borrar todo el HD.

Saludos.
Me parece que no necesitas restaurar nada.

Si no llegaste a la parte de hacer efectiva una nueva tabla de particiones con ese CD de Debian, tu disco ha quedado particionado tal como lo tenias. Sin modificaciones.

Que pasa si inicias la maquina normalmente (con JJ ?) y te fijas con GParted como estan las particiones ?

---

### Post by z37a on 2009-05-23
Recomiendo lo mismo, fijate si en realidad los cambios no se efectuaron, aun así no te preocupes, destruir una tabla de particiones no es problema alguno, conseguite un cd llamado Hyren's boot y con eso podes restaurar la vieja tabla de particiones.

PD: Para tu información es casi imposible eliminar los datos del disco rígido, la única manera 100% efectiva es que lo compactes al hdd y lo partas!!!! Pero podes llegar a formatearlo 10 veces y seguir recuperando gran parte de los datos. Así que no entres en pánico.

---

### Post by leosr on 2009-05-25
Hola.
Lo pude solucionar utizando el programa Testdisk, habia un conflicto con las particiones y lo reparó.
Gracias a todos.

---

