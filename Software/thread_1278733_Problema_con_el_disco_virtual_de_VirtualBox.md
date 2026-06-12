---
title: "Problema con el disco virtual de VirtualBox"
date: 2009-09-29
forum: Software
---

### Post by Hadso on 2009-09-29
Estimados/as:

Había creado una máquina virtual en Ubuntu. Le había cedido 10GB de mi disco. Le instalé XP. Luego, me di cuenta de mi error: dejé todo el disco para el Win. Así que corrí el nuevo Puppy Linux (para probarlo de paso), tomé una porción del disco virtual y la formatee. 

Adios a todo. 

Me dio error, luego aparecía como que todo mi disco virtual estaba sin formato. Adios al Windows. Pero por sobre todo, no me puedo deshacer del archivo vdi (el que simula ser el HD). Es decir, hay 10GB, de mi disco de 80GB, que estan en un limbo, que no me sirven para nada. 
Traté de borrar el archivo desde la consola pero fue inútil, se queda como tildada. Tampoco puedo hacer ls sobre el directorio donde está el archivo. Ni hablar de borrarlo desde el VirtualBox, porque no lo carga más al cuadro con los discos disponibles. 

Que me recomiendan hacer que no impleque formatear todo mi disco real?
Mi objetivo es deshacerme de esos 10GB que han quedado en la nada. 

Desde ya muchas gracias!

---

### Post by pol666 on 2009-10-01
al querer borrarlo desde consola usaste sudo me imagino no? en todo caso podes ir a synaptic, busca virtual box y marca desinstalar completamente, se deberia borrar todo lo que esta adentro de la carpeta de virtualbox.

---

### Post by Hadso on 2009-10-01
> **pol666 said:**
> al querer borrarlo desde consola usaste sudo me imagino no? en todo caso podes ir a synaptic, busca virtual box y marca desinstalar completamente, se deberia borrar todo lo que esta adentro de la carpeta de virtualbox.

Usé sudo, de hecho, el VirtualBox sólo lo podía ejecutar el Root. 
Desinstalé el programa, pero las carpetas están ahí, con el archivo VDI. 

Que puedo hacer para hacerlo desaparecer sin formatear el disco? Gracias!

---

