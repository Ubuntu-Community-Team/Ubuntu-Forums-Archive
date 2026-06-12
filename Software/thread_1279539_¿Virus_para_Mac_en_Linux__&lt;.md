---
title: "¿Virus para Mac en Linux? : &lt;"
date: 2009-09-30
forum: Software
---

### Post by daggaz on 2009-09-30
Hola,
Bueno, es un tema extraño, muy extraño. Ya vi que hay un post que habla sobre esto en «comunidad», pero necesito información y no la he encontrado.
Resulta que en mi tarea de convertir en Linuxeros a mis amigos y familia ya van varios que sin problemas han aceptado Ubuntu, Musix o Fedora. Uno de ellos fue mi hermano.
Tiene una Lap-top Dell con AMD y 1Gb de Ram que aparentemente corre bien con Ubuntu y funcionaba casi todo de maravilla, salvo algunos puntos negativos que nos tenían sin más cuidado (como que el brillo del monitor subía cuando lo bajabas y viceversa); hasta el día de ayer.
Un amigo suyo tuvo un problema en su Mac, algo le cayó y la maquina dejó de funcionar, cosa muy rara también, pues bueno, antes de eso alcanzó a pasarle un archivo a mi hemrnao, me parece que era un «.zip» o «.rar», y desde que llegó el archivo a su computadira algo malo le contagió. 
La ram se encuentra sumamente saturada y de cada diez veces que inicia Ubuntu, una funciona, las demás veces incia automásticamene el apagado, incluso si se ejecuta la terminal de inmediato.
Lo más raro es que muchos de sus archivos y la mayoría de los programas muestran un mensaje como «command not found» o «Error: File not found» y a veces «You are not Root, please close your session» Los muestra como cuadros de diálogo que se pueden repetir infinitamente, no es en la terminal.
Pensé en revisar el disco duro desde el Live CD, pero el disco aparece como bloqueado y no tengo acceso a él.
Pensé en formatear, pero la idea me recuerda a Windos : / y no la paso bien pensando en eso.
¿Alguien tiene alguna recomendación? ¿será esto en verdad un virus o qué?

---

### Post by emiliano_raso on 2009-10-01
Vi el thread de comunidad y no leí nada de eso.
Sin embargo, que los dos estén basados en UNIX no significa que sean iguales.

Te soy sincero: Me parece una pavada :-P Peeeero, todos los dias se aprende algo.

---

### Post by juancarlospaco on 2009-10-01
No, no es un Virus.

Proba el disco con fsck, la ram con memtest, que dice el top ?

---

### Post by emiliano_raso on 2009-10-01
> **juancarlospaco said:**
> No, no es un Virus.

Proba el disco con fsck, la ram con memtest, que dice el top ?

Se un toque mas explicito. Ni yo entendí :-S

---

### Post by juancarlospaco on 2009-10-01
fsck es un programa que viene con Ubuntu que testea el disco que te dice si se estan volando los clusters.
sudo touch /forcefsck && sudo reboot

memtest es un programa que viene con Ubuntu que testea la ram que te dice si se esta pinchando los sectores.
en el Grub esta la opcion

top es un programa que viene con Ubuntu que te dice que ejecutables estan comiendo mas recursos.
top

:)

---

### Post by emiliano_raso on 2009-10-01
> **juancarlospaco said:**
> fsck es un programa que viene con Ubuntu que testea el disco que te dice si se estan volando los clusters.
sudo touch /forcefsck && sudo reboot

memtest es un programa que viene con Ubuntu que testea la ram que te dice si se esta pinchando los sectores.
en el Grub esta la opcion

top es un programa que viene con Ubuntu que te dice que ejecutables estan comiendo mas recursos.
top

:)

Esa es la que vá!
Graciela...
Ahora, que significa qeu te vuelan los clusters? xD

---

### Post by guillermolisi on 2009-10-01
> **emiliano_raso said:**
> Esa es la que vá!
Graciela...
Ahora, que significa qeu te vuelan los clusters? xD
Que el disco rigido esta perdiendo sus propiedades de almacenamiento y comienza a corromper el file systema porque fisicamente esta con problemas u otro componente de hardware, como la controladora, esta funcionando mal.

Cuando un disco SCSI, que levantan mas temperatura que los de otras tecnologias, se cocina comienza a tener problemas de integridad fisica y cuando corres fsck empiezan a salar resortes por todos lados a raiz de lo corrupta que esta su estructura logica.

---

### Post by daggaz on 2009-10-01
O.K.
Bueno, no sé si sea una Pavada. Quizás el Disco Duro sí puede estar dañado; no lo sé. Probaré mañana con esos programas a ver que pasa; sí he visto la opción en el Grub, pero como esta no tuvo Windows no pasa por Grub y no se me había ocurrido. Pero me parece raro eso de los mensajes de error que no terminan y el apagado automático.
Y sé que eso de que sean UNIX no es igual. No sé que pudo haber pasado, mi hermano es muy poco hábil para la computación y no sabe ni qué fue lo que hizo antes de que todo empezara a mal-funcionar.
Aparentemente las dos ultimas acciones fueron tratar de instalar una especie de Nero pero para Linux (?) y abrir ese archivo que menciono.

---

### Post by biale on 2009-10-02
... Faltaría aclarar que era lo que supuestamente tenía ese archivo rar o zip. Si intentó instalar algo (MAC?) o hay trabado un script fallido tendrían que aparecer problemas y no serían problemas de HW ni un virus. Llegó a ingresar en algún momento el "sudo"?

---

