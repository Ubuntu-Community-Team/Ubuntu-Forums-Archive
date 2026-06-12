---
title: "Wine en otra particion"
date: 2009-08-15
forum: Software
---

### Post by krakc on 2009-08-15
Hola

La particion donde tengo instalado el Ubuntu tiene como 1GB libre nada mas, pero tengo pensado instalar unos juegos y programas de windows usando el wine, pero eso sumaria mas de 10GB, entonces queria que me aconsejaran que hacer.

La parte buena es que tengo una particion de 35GB libre para formatear a ext2 

Se puede desinstalar el wine e instalar en esa otra particion y que todos los programas de windows se instalen alli y no me ocupen espacio en la particion que tengo instalado ubuntu ???? si se puede, como lo hago ????

se pueden "fusionar" dos particiones, en este caso, donde tengo ubuntu y la que esta vacia??? si se puede, como lo hago ???

alguna otra mejor idea...???  sin tener que reinstalar ubuntu para reparticionar, que ya bastante me costo configurar todo.

gracias.

---

### Post by Hei Ku on 2009-08-15
Los programas de wine se instalan en tu home, asi que lo que tenes que agrandar es tu home.

---

### Post by krakc on 2009-08-15
> **Hei Ku said:**
> Los programas de wine se instalan en tu home, asi que lo que tenes que agrandar es tu home.

como hago eso sin resinstalar ubuntu... esto es linux, se que debe existir una forma de hacerlo pero ni idea.

---

### Post by Hei Ku on 2009-08-15
Arranca desde un LiveCD y usa el gparted para modificar las particiones. Siempre hace un backup antes.

---

### Post by staar on 2009-08-15
desde las preferencias de wine se puede especificar donde instalar los programas (el falso disco 'C' que crea wine), o también se puede agregar una partición existente como otro 'Disco local' de los de Ventanas, así, podés simplemente crear la partición, montarla donde te guste, y especificarle a wine que instale las cosas ahí o que se la muestre como un disco a los programas de Ventanas...

saludos

---

### Post by EnriqueK on 2009-08-15
Por lo qye entiendo bo tenés tu /home en otra particiónj, por lo que se me ocurren dos soluciones .
1.- La mas inmediata sería que formatees tu espacio disponible en por ejemplo EXT3 , darle permisos al punto de montaje para que no tengas problemas de escritura en esa partición y hacés que dicha partición monte al inicio , el paso siguiente es mover a esa partición la carpeta oculta **.wine** que se encuentra dentro de tu carpeta de usuario y la reemplazas por un enlace simbólico que apunte a la bueva ubicaciónm, con todo esto vas a tener que wine tendrá todo el nuevo espacio a su disposición .
2.- La mejor solución es que nuevas tu /home a esa nueva partición, los detalles te los dejo por que se hace largo de explicar en palabras, pero hay mucha literatura en la red.

---

