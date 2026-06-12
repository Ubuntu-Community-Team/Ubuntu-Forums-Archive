---
title: "Hola a todos !! (no troll)"
date: 2009-06-15
forum: Software
---

### Post by Cajuma on 2009-06-15
Hace varios años vengo usando Windows, y como a todos nos pasa alguna vez en la vida, me puse a buscar alternativas, me encontre en la Red con Ubuntu 9.04 lo baje lo instale, y
aca estoy, lejos de resultarme dificil lo encontre muy ameno y bastante rapido en relacion al xp desatendido que vengo usando. Quiero aprender a utilizarlo a fondo, pero si bien encontre varios tutoriales y corto y pego en la consola para instalar aplicaciones , (lo que no viene por defecto), quiero aprender mas. 
Hasta ahora hice esto [COLOR=Sienna]/Cosas a hacer despues de instalar Ubuntu 9.04 Jaunty Jackalope « Ubuntu Life[/COLOR]. y realmente tengo todo funcionando a full.
La pregunta es ¿ donde puedo encontrar tutos para aprender los comandos basicos ?.
¿Como hago para editar un fichero ? y ¿ por que catzo no encuentro el acento ?
Saludos.......
Cajuma, autodidacta y Kamikaze.........

---

### Post by faktorqm on 2009-06-15
1er sticky del foro: [http://ubuntuforums.org/showthread.php?t=1007750](http://ubuntuforums.org/showthread.php?t=1007750)

tutorial de tutoriales: [http://ubuntu-ar.org/node/198](http://ubuntu-ar.org/node/198)

bienvenido. salu2!

---

### Post by sergiom99 on 2009-06-15
Bienvenido! Llegaste a buen lugar, no te vas a arrepentir.
-Sergio

---

### Post by juancarlospaco on 2009-06-15
No es necesario aprenderse todos los comandos, 
existe Synaptics, Agregar/Quitar, Origenes del Software, 
Gestor de Actualizaciones, Gestor de Drivers Restringidos, etc

Pero la misma Bash te va enseñando lo que necesitas,
si queres saber que hace un programa pones:
man programa
ejemplo: man wget
si queres saber algo a proposito de algun tema:
apropos tema
ejemplo: apropos print
con las teclas de TAB autocompletas los comandos solo tipeando las primeras letras.
Pero no es muy necesario quedarse con solo eso, 
hay maneras graficas de hacer todo tambien, mas si recien comenzas.

Bien, vos decis que necesitas editar un texto,
suponete que estas frente al escritorio de Ubuntu,
y necesitas una Aplicacion, a que Menu vas a ir...?
al de Aplicaciones, y dentro de aplicaciones, tenemos los accesorios,
y dentro de accesorios tenes un icono que dice Editor de Textos,
bueno ya todos sabemos que el Editor de textos suele editar textos,
problema resuelto.


Tu teclado es en Español imagino, tiene Ñ,
suponete que estas frente al escritorio de Ubuntu,
y necesitas modificar una Preferencia en tu Sistema, a que Menu vas a ir...?
al de Sistema, y dentro del de Sistema?, ...al de Preferencias,
y hay ya podes ver el icono de Teclado, hay tenes que entrar,
esa ventana tiene Pestañas, 
pero vos necesitas revisar la Distribucion del teclado,
elejis la Pestaña Distribucion, 
y bueno hay podes ponerle la Distribucion en Español.

Otra cosa que cambia es que aca no hay que hacer el tipico
*"Aplicar--->Aceptar--->Cerrar la ventana para que se aplique el cambio"* 
de Windows, aca solo elejis las opciones y se aplican en tiempo real, 
en la gran mayoria de aplicaciones.

---

### Post by andy_91 on 2009-06-15
> Comandos DOS - LINUX

[Aquí]("http://www.todolinux.com/webs/todolinuxphp/htm/consola/consola_com_dos-linux.php") intentaremos introducirte al mundo de los comandos de la shell de Linux.

Verás que muchos comandos son comunes a MS-DOS, y otros, son muy parecidos.

Verás que estos comandos suelen tener varias opciones. Para saber mas de cada comando, en la shell teclea man ls (por ejemplo para leer sobre el comando ls).

espero eso te sirva ;)

---

### Post by Cajuma on 2009-06-15
Muy agradecido por la bienvenida y por toda la data, el teclado lo tengo configurado en español, pero yo acostumbro a poner el acento con ALT, 130,161 etc. por ahora no pude, pero es un dato menor.
Les cuento que tengo dos HD SATA de 160G. c/u en uno tengo el xp y en el otro instale el
W7 rc y luego el Jaunty 9.04, de curioso nomas tengo el live cd del Kubuntu 9.04 y la idea es Instalarlo en el mismo disco que el Ubuntu, borrando el W7 (espejitos de colores), pero
tengo un problema, en el medio de los dos, hay dos particiones en ext3 vacias, que quiero juntar con la que voy a quitar del W7 y dejar la mitad para cada distro; ¿es factible? ¿ me tocara el grub ? lo estuve intentando desde el live cd, pero no estoy seguro de como hacerlo.
Desde ya muchisimas gracias.........
Cajuma, autodidacta y Kamikaze (pero no como vidrio).........

---

### Post by staar on 2009-06-15
para que podamos ayudarte con el tema de las particiones, posteate la salida de ```
sudo fdisk -l
``` asi vemos mejor como tenés distribuidas las particiones y de que tipo son...

saludos

---

### Post by mama21mama on 2009-06-16
[Manual General de Unix.]("http://rapidshare.com/files/230646207/Comandos_Linux.pdf")

[Manual propio de Ubuntu.]("http://rapidshare.com/files/230646906/ubunturef_esp_.pdf")

Bienvenido

---

### Post by Cajuma on 2009-06-16
Hola de nuevo, aca va la meresunda de particiones:

255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xfb12fb12

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5151    41375376    7  HPFS/NTFS
/dev/sda2            5152       19457   114912945    f  W95 Ext'd (LBA)
/dev/sda5            5152       19457   114912913+   7  HPFS/NTFS

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x2717c543

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        6425    51608781    7  HPFS/NTFS
/dev/sdb2            9736       19457    78091965    f  W95 Ext'd (LBA)
/dev/sdb3            6426        9735    26587575   83  Linux
/dev/sdb5            9736       10260     4217031   83  Linux
/dev/sdb6           10261       19076    70814488+  83  Linux
/dev/sdb7           19077       19457     3060351   82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco
 
Como veran tengo en el segundo disco un berenjenal, y la idea es eliminar el windows 7
e instalar el Kubuntu, la solucion mas rapida es formatear y reinstalar el Ubuntu en una particion y el kubuntu en otra, supongo por lo que vi que al hacerlo compartirian el swap. Pero no me gustaria, ya que el Ubuntu esta a full con actualizaciones y programas instalados, pero si no queda otra me tomare una tarde para hacerlo.
Por lo que vi este foro no es el indicado para estos temas , si le parece bien me paso al foro soft.
Por otro lado estoy tratando de armar una sala de informatica en la Escuela de mis Hijos (Estatal) y le propuse a las autoridades del mismo, ya que no poseen muchas herramientas, y el hard es bastante pobre, formatear todas las maquinas e instalar Ubuntu, Kubuntu o Edubuntu, aunque no seria mala idea el Xubuntu en las maquinas menos potentes, para ello necesitaria contactarme con algun forero de Bariloche que tenga tiempo y ganas de dar una mano........
Me parece una buena forma de introducir a los chicos en Linux ya que todavia no tienen los prejuicios de la gente grande y comoda.
Un abrazo y muchas gracias por el espacio y tiempo que me regalan.
Cajuma, autodidacta y Kamikaze.........

---

### Post by andy_91 on 2009-06-16
para el acento es el botón al lado de la "p" y el arroba *alt gram *y 2 

espero te sirva a mi me sirvió mucho :p

---

### Post by Cajuma on 2009-06-16
Gracias Andy_91 !!! el @ lo uso hace tiempo, con respecto al acento, lo que quiero saber es como configurarlo con:  Ej. ALT 161 = í, son mañas de viejo ya que siempre lo use así. Pero no te preocupes ya me voy a rreglar y les aviso, leete el otro tema, y fijate si te interesa la propuesta.
Saludos........

---

### Post by staar on 2009-06-16
> **Cajuma said:**
> Hola de nuevo, aca va la meresunda de particiones:

255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xfb12fb12

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        5151    41375376    7  HPFS/NTFS
/dev/sda2            5152       19457   114912945    f  W95 Ext'd (LBA)
/dev/sda5            5152       19457   114912913+   7  HPFS/NTFS

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x2717c543

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        6425    51608781    7  HPFS/NTFS
/dev/sdb2            9736       19457    78091965    f  W95 Ext'd (LBA)
/dev/sdb3            6426        9735    26587575   83  Linux
/dev/sdb5            9736       10260     4217031   83  Linux
/dev/sdb6           10261       19076    70814488+  83  Linux
/dev/sdb7           19077       19457     3060351   82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco
 
Como veran tengo en el segundo disco un berenjenal, y la idea es eliminar el windows 7
e instalar el Kubuntu, la solucion mas rapida es formatear y reinstalar el Ubuntu en una particion y el kubuntu en otra, supongo por lo que vi que al hacerlo compartirian el swap. Pero no me gustaria, ya que el Ubuntu esta a full con actualizaciones y programas instalados, pero si no queda otra me tomare una tarde para hacerlo.
Por lo que vi este foro no es el indicado para estos temas , si le parece bien me paso al foro soft.
Por otro lado estoy tratando de armar una sala de informatica en la Escuela de mis Hijos (Estatal) y le propuse a las autoridades del mismo, ya que no poseen muchas herramientas, y el hard es bastante pobre, formatear todas las maquinas e instalar Ubuntu, Kubuntu o Edubuntu, aunque no seria mala idea el Xubuntu en las maquinas menos potentes, para ello necesitaria contactarme con algun forero de Bariloche que tenga tiempo y ganas de dar una mano........
Me parece una buena forma de introducir a los chicos en Linux ya que todavia no tienen los prejuicios de la gente grande y comoda.
Un abrazo y muchas gracias por el espacio y tiempo que me regalan.
Cajuma, autodidacta y Kamikaze.........

jo, que lio de disco :-D, bueno, en realidad no tanto, para hacer lo que querés, te conviene eliminar la partición de windos y las dos de linux que sobran (o si querés dejar una para kubuntu, dejala) y después agrandar la extendida (sdb2) para que ocupe todo el disco, nada más, la swap y la de ubuntu dejalas que no les va a pasar nada...

suerte con el proyecto, te ayudaría, pero me queda un poquito lejos :-D :-D

saludos

---

### Post by Cajuma on 2009-06-16
Gracias Staar, por tu tiempo y la buena Onda, pongo manos a la obra y te cuento.
Un saludo muuuyyyy friooo.

---

