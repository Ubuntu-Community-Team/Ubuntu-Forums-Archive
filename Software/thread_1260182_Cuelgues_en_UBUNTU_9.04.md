---
title: "Cuelgues en UBUNTU 9.04"
date: 2009-09-07
forum: Software
---

### Post by Makkibo on 2009-09-07
Ante que nada, hola a todos y felicitaciones! Soy nuevo en este foro, estuve leyendo un poco y hay cosas realmente interesantes.

Soy bastante nuevo en linux, empecé en mayo con Ubuntu 9.04, y hasta hace unos días venía todo de maravillas.

Si bien he leído sobre problemas similares al que tengo, todavía no doy en la tecla sobre lo que realmente pasa.

EL PROBLEMA:  No puedo utilizar en Ubuntu 9.04 programas basados en Wine o que requieran una alta exigencia gráfica (Ej: No puedo transformar Videos de un formato a otro, No puedo Jugar medal of honor, No puedo instalar ningun juego de windows, En algunos casos el Firefox cuando abro varias ventanas con videos (flash plug))

Las aplicaciones comienzan, pero a los 3 minutos se cuelga todo el sistema. En el caso de traspaso de video aguanta un rato mas. En el caso de Firefox es variable, a veces con dos ventanas, otras con 10 (dejo los video de youtube cargando)

El cuelgue es parcial. Casi siempre se cuelga el entorno gráfico y se bloquea el teclado, pero se puede mover el mouse y el sonido se escucha trabado en un loop de tres segundos. A veces puedo hacer Alt+Bcspc.  y  otras solo puedo hacer REISUB

DATO IMPORTANTE: Antes del 20 de agosto aprox. andaba todo de diez, por esa fecha se actualizo el sistema, kernel a version .15 y empezó el problema que describo.

Mi pc:
Pentium IV 2,56 Ghz, 1GB ram, GeForce 6200 con 256mb. 
Disco de 160Gb, En cuatro particiones, Primaria de 30Gb con Ubuntu en /, la segunda de 2Gb como SWAP, la tercera en EXT4 de 60 Gb montado el /Home,  la ultima  en NTFS no cuenta.
La maquina esta testeada con otro disco rígido en winbugs y anda todo de 10.


Lo que hice hasta ahora fue tratar de volver la actualizacion atras, como no funciono, borré todo y volví a empezar de cero otra instalación (una mentalidad muy WINBUGS)
en un ataque de desesperacion instalé y desinstale millones de cosas. no hubo caso.
En otro intento instale el Karmic Koala alpha 6 recien salido, pasa lo mismo.
Formatee de nuevo y probe con Ubuntu 7 y 8, lo mismo.
Ahora tengo el Ubuntu recien instalado sin actualizaciones, drivers ni nada.

¿Que hago para que funcione como antes?

Desde ya muchas gracias!!

---

### Post by gmunioz on 2009-09-07
Hola mak....:

Para utilizar Medal of Honor necesitas:
    
    * Sistema operativo: WinXP/Vista
    * Procesador: 3,2 GHz
    * Memoria: 2,0 GB
    * Vídeo: 512 MB
    * DirectX 9.0c

Tu ordenador es:

     Pentium IV 2,56 Ghz
     1GB ram, 
     GeForce 6200 con 256mb.

Las distribuciones GnuLinux, son excelentes

pero por ahora no hacen milagros.

---

### Post by pablo.s on 2009-09-07
> **Makkibo said:**
> Las aplicaciones comienzan, pero a los 3 minutos se cuelga todo el sistema. En el caso de traspaso de video aguanta un rato mas. En el caso de Firefox es variable, a veces con dos ventanas, otras con 10 (dejo los video de youtube cargando)

No es recomendable hacer esa práctica
de sobrecargar el sistema con muchos
procesos, sobretodo sobrecargarlo con
el plugin de Adobe Flash, que es harto
conocido por su inestabilidad.
A propósito del transcodificador de video,
cuál programa estás utilizando?

> **Makkibo said:**
> El cuelgue es parcial. Casi siempre se cuelga el entorno gráfico y se bloquea el teclado, pero se puede mover el mouse y el sonido se escucha trabado en un loop de tres segundos. A veces puedo hacer Alt+Bcspc.  y  otras solo puedo hacer REISUB

No hay cuelgues parciales. Lo más
probable es que estés a punto de
quedarte sin memoria RAM y la Swap
esté con la lengua afuera.

> **Makkibo said:**
> Lo que hice hasta ahora fue tratar de volver la actualizacion atras, como no funciono, borré todo y volví a empezar de cero otra instalación (una mentalidad muy WINBUGS)
en un ataque de desesperacion instalé y desinstale millones de cosas. no hubo caso.

Otra práctica que leo muy muy seguido
por aquí. GNU/Linux es un sistema modular,
no es como el MS/Windows, que se corrompe
de forma integra. En GNU/Linux si hay una 
parte del sistema que se daña, se la repara, 
se la reconfigura o cómo mucho se reinstala,
pero solo esa parte. Pero para llegar a eso
es probable que el usuario tenga que llegar
por experiencia propia a la conclusión que
te comento.

> **Makkibo said:**
> En otro intento instale el Karmic Koala alpha 6 recien salido, pasa lo mismo.
Formatee de nuevo y probe con Ubuntu 7 y 8, lo mismo.


Pasando por alto el dato que todavia no salió
la alpha 6, parece que no es un problema de la
actualización de kernel, entonces.

---

### Post by jandry on 2009-09-07
Hola, hay un agregado para firefox (download helper) que te permite bajar los videos de youtube sin necsidad de mantener abiertas las ventanas de navegacion, de caulquier manera deberias tomar el consejo del compañero que me precede y no sobrecargar en demasia el sistema. Abrazo ubuntero

---

### Post by Hei Ku on 2009-09-07
Tambien podrias volver a la version anterior de kernel, si esa te funcionaba.

---

### Post by Makkibo on 2009-09-08
Muchas gracias por las respuestas... 

Efectivamente creo que el problema es de memoria Ram...

A pesar de que lo habia hecho antes de instalar ubuntu y todo estab bien,  nuevamente le hice dos test a la memoria con el CD_LIVE y cuando arranca el UBUNTU 9.04, desde grub.

y en los dos la màquina se colgò, se quedo trabada sin que pueda hacer nada mas que reiniciar. Así que supongo que es eso. 

Cuando pueda comprare una y probarè...MUCHAS GRACIAS...

---

