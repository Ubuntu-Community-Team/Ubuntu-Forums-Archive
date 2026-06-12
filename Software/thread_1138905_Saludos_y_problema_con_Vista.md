---
title: "Saludos y problema con Vista"
date: 2009-04-26
forum: Software
---

### Post by xxalejoxx on 2009-04-26
buenas, me acabo de registrar me encanta el foro, y despues me gustaria seguir con este foro, pero primero necesitaria que alguien muy caritativo y bueno me ayude en esto :P:P

me compre una notebook acer 5738 (esta muy buena) y vino con Vista, :x , entonces me puse a descargar ubuntu 64 bits 8.10, (lo soporta el procesador), hasta ahi todo bien, lo mantuve unos cuantos dias, hasta que mi mama accidentalmente metio un virus en vista, con un pendrive (era un autoejecutable), ese no fue el problema, xq uso nod32, y aparentemente lo habia quitado, no estaba para nada asustado.
entonces, agarro, y hago el mecanismo que usaba para xp, arranco sistema a prueba de fallos, y ahi scaneo todo.
AHI fue el problema, cuando quise ir al sistema a modo a prueba de fallos, al no conocer vista, intente obtenerlo de la misma forma, lo cual no pude hacer, entonces usmeando por ahi encontre (un programa de windows, no uno instalado exterior), una opcion que decia "/SAFEMODE" y la tilde, y me asegure que dijera solo para el proximo reinicio, cosa que si pasaba algo, podia volver. ese fue el peor error de mi vida :(.
reinicio, y desde el grub de ubuntu, cargo "Windows Vista/Longhorn" (el mismo de siempre), y hasta ahi todo bien, pero de una forma rara se carga el loader grafico de windows, no se si me explico, es en el que se muestra la barrita de cargando animada , y que yo sepa, (por lo menos en xp), no se hace eso por si hay un error con el driver de video, para eso "a prueba de fallos" se llama.
entonces sigue cargandose, y derrepente, aparezco en una asquerosa resolucion de 640 * 480 ( se deforma mucho en 16:9 xD) y en medio de esa carga, se reiniciay vuelve a cargarse el grub, vuelvo a intentar elegir Vista, y sigue pasando el mismo circulo vicioso. Por favor ayuda, desde ya muchas gracias ^^

PD: asi tengo las particiones:
hd0,0 una rara particion de vista de como 10 gb que vino de fabrica, es como un sistema de recuperacion de no se que, ya probe bootear desde ese, y no pude
hd0,1 AHI esta la particion real de windows vista de 230 gbs
despues tengo los 2 sda de ubuntu, uno con el disco real de 60 gbs ext3, y el otro el swap, de 2 gbs.
no tengo back up, ahora me arrepiento de no haberlo hecho :(

PD2: sé que es pedir mucho, pero necesitaria una respuesta urgente, por que mi mama la quiere llevar a reparar (cosa que lo que harian los super tecnicos es formatear a la mier...) y no seria muy "reparar" que digamos...


ante cualquier duda sobre algo de mi problema preguntenme y creo que se los voy a poder contestar

---

### Post by staar on 2009-04-26
bueno, esto iría más bien en un foro de windos, pero, por lo que me acuerdo, las opciones de inicio de windos se guardaban en el archivo boot.ini que estaba en el C, por lo menos así era en XP, en vista capaz que es igual...

saludos

---

### Post by xxalejoxx on 2009-04-26
eso mismo busque, pero no lo encuentro, tambien intente editar con el regedit arrancando desde wine, fue uno de los intentos mas desesperados este ultimo xD

---

### Post by sajnox on 2009-04-26
Definitivamente es un problema de windows, si alguien quiere ayudar a xxalejoxx les ruego que lo hagan por mail o mensaje privado

---

### Post by xxalejoxx on 2009-04-26
es que ya se que le problema es definitivamente de windows, pero por eso mismo, como de windows no voy a obtener respuesta alguna al menos que les de 100 dolares de anticipo xD, queria ver si desde ubuntu hay alguna forma de reparalo, xq como ya dije WINDOWS NO LO PUEDO BOOTEAR. y parece que va en camino a el formateo de parte de mi vieja si no le encuentro alguna respuesta

---

