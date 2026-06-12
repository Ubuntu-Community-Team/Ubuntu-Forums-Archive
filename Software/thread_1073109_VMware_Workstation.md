---
title: "VMware Workstation"
date: 2009-02-18
forum: Software
---

### Post by sirkurt on 2009-02-18
bueno esto es una consulta para usuarios avanzados

hace poco vi que estew programa VMware Workstation  abre el sistema operativo completo dentro de otro sistema operativo o sea puedo abrir windows dentro de mi ubuntu siendo realmente windows y no una emulacion como wine, ademas de que soporta aceleracion grafica etc etc.
lo que quiero hacer es instalar esto para gestionar mi red desde windows ya que la otra maquina usa especificamente windows y la uso como " maquina de almacenamiento" por asi decirlo y de esta forma evitarme el laburo de armar la red con samba y tener posibles problemas, ademas obviamente de acceder a programas que uso mucho en windows como photoshop corel etc etc.

es una opcion conveniente o un desastre de idea?

---

### Post by guillermolisi on 2009-02-18
> **sirkurt said:**
> bueno esto es una consulta para usuarios avanzados

hace poco vi que estew programa VMware Workstation  abre el sistema operativo completo dentro de otro sistema operativo o sea puedo abrir windows dentro de mi ubuntu siendo realmente windows y no una emulacion como wine, ademas de que soporta aceleracion grafica etc etc.
lo que quiero hacer es instalar esto para gestionar mi red desde windows ya que la otra maquina usa especificamente windows y la uso como " maquina de almacenamiento" por asi decirlo y de esta forma evitarme el laburo de armar la red con samba y tener posibles problemas, ademas obviamente de acceder a programas que uso mucho en windows como photoshop corel etc etc.

es una opcion conveniente o un desastre de idea?
Algunas aclaraciones:

Wine *no es un emulador*, es un entorno de trabajo acondicionado para correr aplicaciones Win. De hecho Wine es una sigle que significa **W**ine **I**s **N**ot an **E**mulator.

Por ahora, la virtualizacion de maquinas con el software disponible en el mercado *no* permite aceleracion grafica 3D full ya que una de las principales virtudes de esta tecnologia es la de la abstraccion de hardware respecto del host donde corren (lo cual trae muchisimas ventajas y algunas, como la falta de 3d, desventajas).

No termino de entender bien la problematica que queres resolver con virtualizacion y que tipos de problemas queres evitar con esto (generalmente, comparando alternativas, algunos problemas se evitan en pos del riesgo de tener que resolver otros. No hay una solucion perfecta). Tal vez alguna breve explicacion del entorno de trabajo y las necesidades a resolver ayuden a comprender mejor la situacion.

---

### Post by sirkurt on 2009-02-18
basicamente lo que quiero es ejecutar programas de windows y posiblemente juegos
por eso entonces la pregunta seria si es conveniente usar este programa para hacerlo de forma mas cencilla ya que Wine no me esta abriendo ningun exe nose porque

---

### Post by guillermolisi on 2009-02-18
> **sirkurt said:**
> basicamente lo que quiero es ejecutar programas de windows y posiblemente juegos
por eso entonces la pregunta seria si es conveniente usar este programa para hacerlo de forma mas cencilla ya que Wine no me esta abriendo ningun exe nose porque
Contar con una Vm corriendo Win es como tener una PC aparte (con cierto impacto en el rendimiento del host que alberga a la VM). O sea, vas a poder hacer todo lo que haces con una PC fisica con Win salvo utilizar aceleracion de video 3D con lo que el tema juegos, por ejemplo, quedara limitado por esta restriccion.

---

### Post by sirkurt on 2009-02-18
lo que mas me interesa por el momento es correr photoshop y otros programas de diseño asi que etiendo que mientras no sea conjuegos, o almenos juegos pesados puedo correr bien estas aplicaciones

---

### Post by guillermolisi on 2009-02-18
> **sirkurt said:**
> lo que mas me interesa por el momento es correr photoshop y otros programas de diseño asi que etiendo que mientras no sea conjuegos, o almenos juegos pesados puedo correr bien estas aplicaciones
Si, es asi siempre que los programas de diseño no requieran de aceleracion grafica completa.

Considera que configuracion de RAM le darias a la VM con Win, que tamaño de disco o discos y que procesador tiene la PC donde vas a virtualizar para que no se achanche cuando levantes la VM.

---

### Post by sajnox on 2009-02-18
> **sirkurt said:**
> basicamente lo que quiero es ejecutar programas de windows y posiblemente juegos

En mi opinion levantar una VM para jugar linda con lo ridiculo, cuanto tardas en reiniciar? 40 segundos, 1 minuto?

No creo que zafar de windows sea levantar una maquina virtual dentro de ubuntu.

Si queres virtualizar para los programas que decis te recomiendo que pruebes con Virtualbox [0], en mi experiencia es mas facil de usar y configurar. Ademas tenes mucha gente de aca que lo usa y seguro que te puede dar una mano.

Saludos


[0] [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

