---
title: "¿Alguien sabe cómo conectar en red una Mac y Ubuntu?"
date: 2009-10-23
forum: Software
---

### Post by cor_stellae on 2009-10-23
Estoy tratando de compartir mis discos duros en una máquina con Ubuntu 9.04, para verlos desde una portátil Mac. Supuestamente se puede hacer mediante un programa que se llama Netatalk, pero no logro comprender cómo se hace. Tampoco he logrado encontrar tutoriales lo suficientemente sencillos para mí. ¿Alguien lo ha hecho ya? ¿Alguien me puede guiar en el proceso?

---

### Post by albandy on 2009-10-23
¿Has probado a compartirlo mediante samba?

---

### Post by cor_stellae on 2009-10-23
He aquí mi dilema: tengo muchos meses de no tocar una consola en Ubuntu y el día de hoy estoy que no entiendo nada de nada. Ya logré, parece, instalar Samba, pero no logro entender cómo se configura. En otro foro, un usuario dice que con solo compartir su computadora en Samba, su red inalámbrica reconoció la computadora sin problemas.
Entonces mi pregunta es: ¿Cómo configuro Samba? Hoy necesito una de esas guías para dummies que le dicen a un ignorante de programación cómo programar... ](*,)

---

### Post by pablo.s on 2009-10-23
Puedes compartir carpetas de un
sistema al otro mediante NFS.
Hay un tutorial muy bueno para
Ubuntu [aqui]("http://ubuntu-ar.org/node/208") y para Mac OS X hay
información [aqui]("http://www.macosxhints.com/article.php?story=20090830073912179").

---

### Post by juancarlospaco on 2009-10-23
**SSH**
*Rapido, facil, seguro, eficiente.*

---

### Post by cor_stellae on 2009-10-23
Hola Pablo:

Seguí el tutorial, pero no he pasado de la instalación. Al llegar a "En este caso se compatirá la carpeta..." etc, ¿significa que para compartir cualquier carpeta o disco duro tengo que seguir este mismo procedimiento doloroso por la vía de la consola? ¿No hay una forma de simplemente indicar que los discos duros íntegros se comparten?

Y ahora, la otra cosa: una vez que uno logra "compartir" los discos duros de Ubuntu, ¿cómo accedo a la computadora desde la Mac? ¿Alguien sabe? :confused:

Juan Carlos... ¿qué es el SSH?????? :(

---

### Post by pablo.s on 2009-10-23
> **cor_stellae said:**
> ¿significa que para compartir cualquier carpeta o disco duro tengo que seguir este mismo procedimiento doloroso por la vía de la consola? ¿No hay una forma de simplemente indicar que los discos duros íntegros se comparten?

Por una cuestión de seguridad se
hace imposible que discos duros
en su totalidad se compartan.
No obstante puedes compartir el
directorio /home de tu maquina
Ubuntu y ahí creo que tienes
bastantes carpetas.

> **cor_stellae said:**
> Y ahora, la otra cosa: una vez que uno logra "compartir" los discos duros de Ubuntu, ¿cómo accedo a la computadora desde la Mac? ¿Alguien sabe? 

Hay que configurar NFS para la
Mac también. ¿Qué versión del
Mac OS X tienes? 10.4 o 10.5?
No creo que tengas el último, 
aunque también puede ser.

---

### Post by juancarlospaco on 2009-10-23
Tiene razon Pablo es por una cuestion de seguridad que es medio vueltero compartir *"discos COMPLETOS"*.

pero we..., 
de lo que he probado SMB el protocolo de windows, es lento, 
llena la red de spamm de paquetes, y no le fio mucho.
NFS esta bueno, es seguro y eficiente, necesitas mucho de CLI, 
pero terminas tocando todo el sistema para hacerlo andar.
SSH esta bueno, es seguro y eficiente, y solo necesitas hacer [click aca]("apt:/openssh-server") en ubuntu,
despues te conectas a la PC con ese protocolo, 
por CLI, por GUI, por X, por lo que venga, una VPN ad-hoc.

---

### Post by cor_stellae on 2009-10-24
Hola chicos:

Ayer tuve que irme, pero hoy sigo en pie de lucha tratando de comunicar mis dos computadoras.

Pablo, la computadora que estoy tratando de vincular tiene Leopard 10.5.8. 

Juan Carlos, hice clic en el vínculo, pero Firefox no sabe qué hacer con él. Dice que el protocolo (apt) no está asociado con ningún programa.

Sigo igual que ayer, sin saber cómo hacer reaccionar al Ubuntu para vincularlo a una red. Por ahora, estoy tratando de armar una red máquina a máquina, con cable Ethernet. La idea, más adelante, será vincular tres computadoras (dos con Ubuntu y una Mac), en una red inalámbrica.

---

### Post by guillermolisi on 2009-10-24
> **cor_stellae said:**
> Hola chicos:

Ayer tuve que irme, pero hoy sigo en pie de lucha tratando de comunicar mis dos computadoras.

Pablo, la computadora que estoy tratando de vincular tiene Leopard 10.5.8. 

Juan Carlos, hice clic en el vínculo, pero Firefox no sabe qué hacer con él. Dice que el protocolo (apt) no está asociado con ningún programa.

Sigo igual que ayer, sin saber cómo hacer reaccionar al Ubuntu para vincularlo a una red. Por ahora, estoy tratando de armar una red máquina a máquina, con cable Ethernet. La idea, más adelante, será vincular tres computadoras (dos con Ubuntu y una Mac), en una red inalámbrica.
Y por que no empezas vinculando las dos que tienen Ubuntu y de paso te familiarizas con el contexto y procedimiento ? Con esa experiencia despues encaras la Apple.

---

