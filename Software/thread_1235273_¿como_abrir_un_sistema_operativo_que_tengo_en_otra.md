---
title: "¿como abrir un sistema operativo que tengo en otra partición?"
date: 2009-08-08
forum: Software
---

### Post by pelaolinux on 2009-08-08
Hola a todos!
me gustaría saber si hay alguna forma de abrir el otro sistema operativo que tengo instalado en mi ordenador en una partición diferente a la que tengo instalado el sistema operativo ubuntu!!
me gustaría saber si se puede hacer eso con  algún programa para abrir el otro sistema operativo dentro de ubuntu!!!
Saludos! 
y saludos en especial al señor Carlos C, que siempre participa en todas las preguntas que escribo en el foro.

---

### Post by AlexDDR on 2009-08-09
con el otro sistema operativo te refieres a windows¿? o a otro linux, bsd , etc? especifica mas cual es el problema y será mas facil que te respondan

saludos

---

### Post by pelaolinux on 2009-08-09
> **AlexDDR said:**
> con el otro sistema operativo te refieres a windows¿? o a otro linux, bsd , etc? especifica mas cual es el problema y será mas facil que te respondan

saludos


mira te explico!!
lo que susede es que en el ordenador tengo dos particiones, una de ellas tiene windows xp y la otra tiene ubuntu 9.04, lo que sucede es que yo quiero abrir el windows xp desde linux pero quiero abrir el mismo que ya tengo instalado en la otra particion. por que yo puedo utilizar windows xp desde ubuntu con el programa VirtualBox pero ese programa me dice que tengo que instalar windows desde una imagen y alfinal es como si instalara windows dentro de ubuntu y eso es lo que no quiero, por que yo necesito abrir el otro windows que ya tengo instalado en la otra particion...

me entiendes ahora ??? 

saludos!!! 
[B]
[/B]

---

### Post by AlexDDR on 2009-08-09
generalmente el instalador de ubuntu reconoce automaticamente windows y lo agrega el menu del boot que te permite elegir  el sistema operativo y se llama grub


en una consola pon 

sudo fdisk -l

y pega el resultado acá en el foro


saludos

---

### Post by pelaolinux on 2009-08-09
> **AlexDDR said:**
> generalmente el instalador de ubuntu reconoce automaticamente windows y lo agrega el menu del boot que te permite elegir  el sistema operativo y se llama grub


en una consola pon 

sudo fdisk -l

y pega el resultado acá en el foro


saludos



disculpa pero yo me refiero a poder manipular ese windows con la misma forma como manipulo un windows con el virtualBox.... 
disculpa por las molestias !!!!

---

### Post by nopersona on 2009-08-09
> **pelaolinux said:**
> disculpa pero yo me refiero a poder manipular ese windows con la misma forma como manipulo un windows con el virtualBox.... 
disculpa por las molestias !!!!

Y la utilidad de ello sería?

---

### Post by AlexDDR on 2009-08-09
de poder se puede, pero es un proceso complicado en que hay que jugar con los perfiles de hardware de windows en el administrador de hardware y no es muy seguro, ya que la maquina virtual no usa hardware real de tu maquina sino uno virtual tambien, entonces no se que tan seguro sea o que tan facil, porque es un procedimiento engorroso y talvez inestable.


lo mejor es usar una instalacion de WINDows y compartir una carpeta por red entre los sistemas operativos tal como se dice en tdos los manuales


saludos

---

### Post by Carlos C on 2009-08-10
Si, tiene razón AlexDDR, es engorroso lo que quieres, nunca lo he intentado pero me imagino la cantidad de problemas que eso traería. Te sale más fácil usar un booteo dual o instalar un windows mediante virtualbox o compartir una carpeta o montar la partición de windows, etc.

---

### Post by moFeta on 2009-08-15
Se puede, no es TAN complicado hacerlo, el problema es lo que te dicen, winpork se crea un perfil para un determinado hardware y si se lo modifican, simplemente no arranca, lo más habitual es por el sistema de video, ya que si por ejemplo, está configurado para usar ATI, no la encuentra y por lo tanto no va. 
A mi no me funcionó, pero si te sirve, las indicaciones están en varias partes, yo usé lo que sale en este blog: [casidiablo]("http://casidiablo.net/correr-windows-preinstalado-sobre-ubuntu/").
Lo único que logre hacer funcionar es crear el disco virtual enlazado a una partición de un disco duro real, y allí instalar, desde virtualbox, windows xp. Eso si me funcionó, pero no le veo mayor conveniencia a usar un disco virtual completo. Lo único sería para usar un Win preinstalado en un equipo, y que sea 'legal'.

Suerte

---

### Post by AlexDDR on 2009-08-15
lo voy a probar, espero no provocar ningun problema en windows , pero e fin todo sea por la ciencia

---

### Post by EnriqueK on 2009-08-15
Se puede co VMWare Worktation (VirtualBox no tiene esta opción), nunca lo hice, pero al parecer no parece ser complicado , aquí un tuto que te puede servir 
[http://www.kriptopolis.org/virtualizar-una-particion-windows-ya-existente](http://www.kriptopolis.org/virtualizar-una-particion-windows-ya-existente)

---

