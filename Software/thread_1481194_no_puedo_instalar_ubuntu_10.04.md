---
title: "no puedo instalar ubuntu 10.04"
date: 2010-05-12
forum: Software
---

### Post by hellhell321 on 2010-05-12
Hola a todos, soy nuevito en esto y tengo un problema que por ahi es simple
me baje la imagen de ubuntu-10.04-desktop-i386, la grabe en un cd
y cuando va a arrancar la instalacion o eso me parece me salta este cuadrito
 
[IMG]http://i40.tinypic.com/2cok0t4.jpg[/IMG]
 
despues de este cartel, me deja entrar al escritorio pero anda muy lento o directamente se tilda y no va..
 
como dije, soy nuevo y no tengo ni la mas remota idea de como solucionar esto o porque 
no puedo instalarlo.. alguna idea???

---

### Post by Sarum001 on 2010-05-12
Una vez me saltó ese mismo error cuando probaba una versión alpha de Lucid. Lo solucioné volviendo a grabar la imágen en otro CD, pero a la menor velocidad que (El programa que uses para quemar cd)te permita. Esto se supone que es para evitar errores en la grabación. 

También probaría bajar una nueva imágen ISO, por si la que tenés no se bajó del todo bien.

Saludos y no te pierdas. :P

---

### Post by hellhell321 on 2010-05-12
bueno, al final la instalacion la pude hacer, tardo mucho fue bastante lenta.. pero ahora el problema de la instalacion quedo atras y aparecio uno nuevo, TODO funciona muy lento pero lento de verdad.. la interfaz va muy lenta, abrir el firefox tardo una eternidad por ej. abrir el monitor de procesos lo mismo, lenta la interfaz y tarda en cargar. 

vos decis que vuelva a bajar otra imagen, queme y reinstale.. funciona? por la dudas aca dejo datos de la pc y alguien quiza tiene idea que pasa.

ASUS A8V
Athlon 64 +3000
2gb de ram
gforce MX 4000 128mb

bueno, gracias Sarum001 no me pierdo por aca me quedo, y si alguien quiere y puede darme una mano gracias.

(mira que lento me va, que escribir esto me llevo 20min) :S

---

### Post by jamoncillo on 2010-05-12
ouch.
me paso eso tambien, cuando migré al 9.04 de 8.10. lo solucioné haciendo una reinstalacion limpia. Estas intentando un upgrade? o borraste el disco duro antes de instalar?

el error que te salia efectivamente viene de un error en la imagen del disco. Si te da problemas al correrlo desde el cd, tienes 2 opciones (ademas de la ya mencionada, de regrabar la imagen):
1) ordenar un cd directamente de Ubuntu (pfff... esperar a que te llegue)
2) carga la imagen del disco a una usb
 para este ultimo. si estas dentro de ubuntu puedes usar unetbootin para que la cree por ti (primero habilitando en el BIOS la opcion de inicio via USB)
fuera de ubuntu... la verdad no se muchas opciones =/   me desconecte de windows hace tiempo. lo ultimo que hice ahi fue crear un xp booteable de usb y fue un des**dre

---

### Post by jamoncillo on 2010-05-12
por cierto, las especificaciones de tu maquina estan de maravilla, no deberia darte problemas por ello. 

Olvide peguntar: estas probando 32 o 64bits?

---

### Post by hellhell321 on 2010-05-12
bueno, al final fue algo simple... con un poco de paciencia solucione el tema, me puse a investigar las opciones del sistema, cambie la resolucion de pantalla y mejoro un poquito, tambien baje e instale (fue automatico [-o< ) el controlador para nvidia y por ahora anda bien, la interfaz anda 10 puntos y las aplicaciones se abren re rapido.

jamoncillo baje la de 32bits, no entiendo bien la diferencia.. instale ubuntu por tanto ruido que viene haciendo y probar algo nuevo y desconocido hasta ahora para mi, borre el windows xp que tenia y ahora solo tengo ubuntu. lei por ahi que es bueno tener los dos sistemas hasta adaptarse pero creo que me voy adaptar mejor si lo uso todo el tiempo y supongo que tambien voy a aprender un poquito mas de esto, igual tranqui para mi la pc es musica, fotos, videos, msn.  

Sarum001 despues voy a bajar otra ISO como vos decis por la dudas y jamoncillo gracias tambien. 


:D

---

### Post by jamoncillo on 2010-05-12
que bien, hellhell321 !
la diferencia entre la de 32 bits y 64 radica en el procesador. Muchos procesadores (incluyendo el tuyo, AMD64 [que, como su nombre lo indica, es de 64 bits]) pueden... llamemosle 'manejar' mas informacion a la vez, que los de 32 bits. Esto se nota radicalmente en la RAM. Uno de 32bits puede manejar solamente 4Gb en ram. Si tu compu tuviera mas de eso, necesitas instalar el OS de 64bits, que es el que puede direccionarlas (controlarlas, digamos).

Esta bien si dejaste el de 32. Si metias el de 64, tambien. No hay mucha diferencia realmente, excepto con algunas aplicacines que pueden o no correr

Te preguntaba al respecto porque a mi el problema que tienes me surgio al instalar el de 64 bits. Regrese a 32bits y corrio de maravilla.

Y que bueno que hayas cambiado completamente a Ubuntu. Creo que no te arrepentiras. Cualquier otra cosa que necesites referente, estoy para ayudarte (=  No soy muy ducho tampoco, pero hago lo posible por arreglar los problemillas que me van surgiendo sobre la marcha

---

### Post by Sarum001 on 2010-05-12
vamo' nomá' si queres!!!
Me puse contento :lolflag:

Según lo veo, ahora, me parece que el tema de la ISO no es tan crucial-Aunque siempre es bueno contar con una imágen "sana" del SO a la hora de instalar- sinó que la mano venía por el tema de las arquitecturas y los  drivers. Podés probar para sacarte la duda.

Saludos.

---

### Post by alfplayer on 2010-05-12
En realidad, Ubuntu para 32-bit puede usar más de 4 GB de RAM si se usa un kernel con PAE, que se puede instalar fácilmente.

---

### Post by jamoncillo on 2010-05-12
> **alfplayer said:**
> En realidad, Ubuntu para 32-bit puede usar más de 4 GB de RAM si se usa un kernel con PAE, que se puede instalar fácilmente.

yupe, muchas gracias por la aclaracion (=

---

