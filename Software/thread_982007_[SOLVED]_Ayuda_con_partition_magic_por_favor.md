---
title: "[SOLVED] Ayuda con partition magic por favor"
date: 2008-11-14
forum: Software
---

### Post by julianch89 on 2008-11-14
hola a todos .. les paso a comentar .. yo antes tenia windows nada mas y dps instale ubuntu .. y ahora me baje el partition magic 8 para windows  y me tira el error 117  "partition's drive letter cannot be identified " ... antes no me pasaba y queria saber si  era algo de linux o por lo menos como solucionarlo .. por q probe el mismo programa  en otra maquina sin linux .. y me anduvo .. por favor el que me pueda ayudar vendria barbaro ... desde ya muchas gracias .. 

julian ..

---

### Post by Thalskarth on 2008-11-14
Supongo que debe deberse al tema de que el Partition magci es de windows y no debe reconocer bien las partciones de linux...

Te recomiendo el [parted magic ]("http://partedmagic.com")
o mismo, podes usar el LiveCD de Ubuntu, que trae el programa Gparted (editor de particones) para trabajar, editar, crear o borrar particones

saludos

---

### Post by sajnox on 2008-11-14
Te pregunto que es lo que queres hacer con el partition magic?, para que lo instalaste?. Cual es la particion que no te reconoce?.

---

### Post by julianch89 on 2008-11-20
era por q me paso de maquina y la otra la queria dejar con el windows nada mas .. y en esa maquina tengo ubuntu y windows (mitad y mitad de disco).. y al correr por windows el partition magic 8 .. o versiones anteriores me aparece ese error .. y por lo que estuve viendo ya es bastante conocido .. igual si no no hay drama...consigo el cd de xp  y desde ahi arreglo todo .. era para ver si hay forma de solucionar ese problema para que me funque el partition magic .. gracias

---

### Post by hernan blau on 2008-11-20
Cuando uses Ubuntu el privativo ya no lo querrás. Deja de ser esclavo del monopolio y sé libre. HB.

---

### Post by EnriqueK on 2008-11-21
¿Que sistema de archivos estás usando en Linux?, al EXT lo reconoce perfectamente, no creo el partition magic  reconozca Reiserfs u otros, esto lo digo por que algo parecido me pasó cuando instale PC BSD , el partition magic si bien no me indicaba error, me mostraba todo el disco sin particionar.

---

### Post by WanderingKnight on 2008-11-21
Con gparted desde el Live CD de Ubuntu podes hacer exactamente lo mismo que con el Partition Magic...

---

### Post by pachux on 2008-11-30
Hola aprovecho este hilo porque quiero usar el gparted y no me deja achicar la partición con wind.
Tengo un disco con una sola partición de 160 gb (ntfs) estoy usando el cd de kubuntu 8.10. loq ue veo es que el gparted me da que no está montada la unidad (?).
¿Por donde empiezo??

---

### Post by c4d0rn4 on 2008-11-30
que raro! =S, en realidad se queja si la partición está montada; si mal no recuerdo.

---

### Post by Hei Ku on 2008-11-30
Si. No podes hacer cambios en el gparted si la particion esta montada. Asi que vas bien.

---

### Post by pachux on 2008-11-30
Listo. ya está. El error fué que había que correr el comando chkdsk desde wind porque había errores.
Recomiendo a todos los novatos (como yo) verificar esto antes de particionar.
Gracias

---

