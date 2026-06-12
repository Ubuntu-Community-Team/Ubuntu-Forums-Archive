---
title: "Ayuda - Como instalar Ubuntu en otro disco"
date: 2010-10-06
forum: Software
---

### Post by manodigital on 2010-10-06
Hola amigos, necesito ayuda para no hacer macanas antes de instalar Ubuntu Lucid en otro disco duro, les cuento, tengo windows 7 en un SATA, agregué un disco de 80 IDE en donde quiero instalar Ubuntu, y una grabadora de DVD como eslave en al misma conexión ide.
Ahora bien, en realidad quiero tener la misma opción que cuando tenia un disco solamente, que tengo la opcion con el grub de arrancar el sistema que prefiero en ese momento, pero tengo mis dudas como hacerlo al querer instalar Ubuntu en el disco de 80. 
Alguien me podría pasar un tutorial o un link de alguna página que me ayude a hacerlo?
He buscado bastante, pero no encuentro algo claro como para realizarlo.
No soy tan newbie con Ubuntu porque ya hace 3 años que lo vengo usando, pero como tengo dudas y antes de instalar y hacer macanas recurro a los master´s de aquí.
desde ya, muchas gracias por su interés y sus respuestas.

slds. Osvaldo :)

---

### Post by hectorivand on 2010-10-06
Instalalo desde el cd, seleeciona el disco de 80, instalalo, Grub se va a instalar y luego te va a dar la opción de con que sistema arrancar.

Es lo mismo que instalandolo en un solo disco, los dos sistemas.

Saludos
Nacho

---

### Post by manodigital on 2010-10-07
:P muchas gracias Nacho por tu respuesta, pero no configura el arranque dual, la pc sigue arrancando con windows, y lo que quiero es mantener el arranque igual que si tuvieras un solo disco, que aparezca el menú del grub, con la posibilidad de elegir que sistema operativo arrancar, voy a seguir buscando para ver si encuentro algo sencillo de realizar.

---

### Post by asterix77 on 2010-10-07
¿Eso quiere decir entonces que no puedes entrar a ubuntu porque no te aparece el grub con sus opciones de arranque?


Saludos

---

### Post by hectorivand on 2010-10-07
> **manodigital said:**
> :P muchas gracias Nacho por tu respuesta, pero no configura el arranque dual, la pc sigue arrancando con windows, y lo que quiero es mantener el arranque igual que si tuvieras un solo disco, que aparezca el menú del grub, con la posibilidad de elegir que sistema operativo arrancar, voy a seguir buscando para ver si encuentro algo sencillo de realizar.

Algo te falto, lo instalaste con los dos discos enchufados?

No importa, hace que bootee el disco que tiene linux y segui estas instrucciones.:

[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)

Contanos.

Saludos
Nacho

---

### Post by manodigital on 2010-10-07
> **asterix77 said:**
> ¿Eso quiere decir entonces que no puedes entrar a ubuntu porque no te aparece el grub con sus opciones de arranque?


Saludos


exacto! :(

---

### Post by alfplayer on 2010-10-07
Instalaste Ubuntu con ambos discos conectados? En qué disco elegiste instalar el cargador de arranque durante la instalación de Ubuntu?

---

### Post by asterix77 on 2010-10-07
Al parecer algo pasó con el grub durante la instalación. Para recuperarlo vas a tener que usar un live cd y seguir las instrucciones del link que te pasó hectorivand.

Lucid posee grub 2 por lo que tendrás que seguir las instrucciones a partir del apartado..

** Grub 2 **

 ** Usando una distribución Live **

Saludos

---

### Post by alfplayer on 2010-10-07
Si se hizo algo incorrecto en la instalación, lo más fácil es reinstalar.

---

### Post by manodigital on 2010-10-08
> **alfplayer said:**
> Instalaste Ubuntu con ambos discos conectados? En qué disco elegiste instalar el cargador de arranque durante la instalación de Ubuntu?

Antes de contestar, lo primero que quiero hacer es agradecer todas las respuestas que he recibido, la verdad, impresionante.

Así es, con ambos discos conectados y elegí instalar el cargador de arranque en el de windows, ya que en la ultima opcion antes del formateo e instalacion si entras en avanzadas está tildada por defecto la opcion del disco 0.

voy a seguir intentando antes del 10.10 

slds.

---

### Post by alfplayer on 2010-10-08
Si se puede iniciar windows probablemente es porque se sigue iniciando el cargador de inicio de windows, o sea, pareciera que Ubuntu no instaló el cargador de inicio en el disco de windows. Si se instaló en el otro disco, para usar el nuevo menú de inicio habría que cambiar el orden de inicio de los discos rígidos en el BIOS.

---

### Post by manodigital on 2010-10-08
> **alfplayer said:**
> Si se puede iniciar windows probablemente es porque se sigue iniciando el cargador de inicio de windows, o sea, pareciera que Ubuntu no instaló el cargador de inicio en el disco de windows. Si se instaló en el otro disco, para usar el nuevo menú de inicio habría que cambiar el orden de inicio de los discos rígidos en el BIOS.

Ah, Ok, entonces voy a probar nuevamente y lo comento :)

---

