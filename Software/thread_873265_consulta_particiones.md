---
title: "consulta particiones"
date: 2008-07-28
forum: Software
---

### Post by Barasuishou on 2008-07-28
hola bueno hace un buen tiempo tengo isntalado con el wubi ubuntu, pero ahora lo quiero instalar posta, no voy a volar windows por que bueno lo requiero para algunos progs de la facu XP, peeero voy a achicar la particion de windows para hacer la de ubuntu, mi disco es de 150gb, yo pensaba hacer, unos 70gbs u 80gbs, para ubuntu y lo que sobra para windows(tengan en cuenta que los juegos voy a tenerlos en ambas particiones, osea los nativos de ubuntu en ubuntu los de win en win, excepto alguno que otro que voy a probar ocn el wine), y tengo un 1gb de RAM, había leido por ahí que la "partición de intercambio" de ubuntu iva de acuerdo a la RAM y por lo qeu recuerdo en mi caso debía ser de 1gb, está bien???, solo por si la dudas el ubuntu que instalo es de 64bits, nose si cambia en algo pero porai necesito una partición de intercambio más grande o algo :S, bueno a ver que les parece hago como dije???, 80gbs ubuntu, resto win, y 1gb particion de intercambio???

---

### Post by Hei Ku on 2008-07-28
1GB de swap esta bien. Y si sos nuevito en Ubuntu quizas te convenga la de 32 bits, porque a veces la de 64 tiene menos paquetes precompilados.

---

### Post by pol666 on 2008-07-29
Si vieja, no va a haber drama con esa organizacion, pero te conviene 32 bit como dijo el amigo.

Tambien si queres podes hacerte una /home en otra particion para guardar datos y configuraciones y no perderlas cuando instales una version nueva de ubuntu

---

### Post by Tosh78 on 2008-07-29
Aprovecho esto, para hacer una consulta yo. Mi caso es muy similar, salvo que me gustaria montar el home en una particion a la que tambien tuviera acceso wingarch, que me recomiendan? Tengo 2gb de ram y un disco de 160.

---

### Post by Thalskarth on 2008-07-29
> **Tosh78 said:**
> Aprovecho esto, para hacer una consulta yo. Mi caso es muy similar, salvo que me gustaria montar el home en una particion a la que tambien tuviera acceso wingarch, que me recomiendan? Tengo 2gb de ram y un disco de 160.

Create la particion para el home en ext3 como vos desees.

y luego con al windows instale este driver desde [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/) y entonces te va reconocer las partciones ext3 (las que vos quieras). configurar el driver para que te carge la particion del home (fijate en las propieadas de setear todo a UTF-8 asi funcan bien los acentos) y listo.

---

### Post by Barasuishou on 2008-07-30
bueno a ver al final no me dejaba modificar la partición de windows, y mande formateo total y linux en todo el disco, ahora les pregunto a ver si tienen una solución para esto, ni me molesto en poner otra vez windows, necesito una forma de hacer andar en ubuntu el 3d studio max(en su última versión), y el flash professional(o algun editro para linux de .fla y .as), si me dicen como hacer andar o uan forma de tenerlos en ubuntu, le puedo decir chau por completo a windows :D

---

### Post by Tosh78 on 2008-07-30
Yo intentaria con WINE. Te fijaste si esos programas estan soportados? Yo instale algunas cosas con WINE, asi que si llegas a tener algun problema, avisame e intento darte una mano.
Para instalar wine lo podes hacer desde synaptic o desde la consola con sudo aptitude install wine
Avisa que tal te fue.

---

### Post by Barasuishou on 2008-07-30
por ahora probe con el 3dstudio max, y me tira un error en la instalación :S, que no pudo implementar backburner algo así¿?

---

### Post by Tosh78 on 2008-07-31
Una opcion que a mi me resulto cuando tambien recibia errores en la instalacion de un juego, es instalarlo en wingarch, y despues te copias el directorio en el que lo instalaste en wingarch (generalmente, Archivos de programas\nombredelprograma) y lo pegas en el directorio que te genero WINE en ubuntu.
Para esto ultimo, podes entrar en tu home, en ver, seleccionas la opcion que te permite ver archivos y carpetas ocultos. Ahi vas a ver la carpeta .wine
Entra en esa carpeta, entra la carpeta que dice algo asi como drive_c, y ahi vas a encontrar Archivos de programa. Ahi pega lo que te copiaste de wingarch.
A mi eso me funciono.

---

