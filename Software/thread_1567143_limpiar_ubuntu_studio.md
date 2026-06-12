---
title: "limpiar ubuntu studio"
date: 2010-09-03
forum: Software
---

### Post by joseluis on 2010-09-03
amigos, hace un tiempo instalé Ubuntu Studio,y la verdad es que ahora, después de unos meses, me doy cuenta de que no necesito semejante distro, y querría quedarme solo con ubuntu pelado.
La cosa es que no quiero formatear y reinstalar, porque hay programas y configuraciones que quiero mantener.
Ahora bien, ¿como se hace para "volar" todo lo que trae Studio de un golpe? asi liberaría espacio y dejo lo que en verdad me sirve.

Espero haber sido claro. 

gracias

---

### Post by guillermolisi on 2010-09-03
Tomas nota de cuales son los paquetes/programas que no queres utilizar mas y los desinstalas, removiendolos completamente, usando Synaptics.

Tendrias que verificar que kernel estas usando ya que el que corresponde a UStudio, mas alla de la version, es RealTime y Ubuntu desktop (la que entiendo queres volver a tener en tu maquina) usa kernel Generic.

Para saber que kernel estas usando, en una terminal/consola ingresas ```
uname -a
``` y ahi te dice, entre otras cosas, que version y tipo de kernel estas corriendo.

---

### Post by joseluis on 2010-09-03
guillermo..gracias
¿en qué me modifica el tema del kernel? es decir, ¿en qué me puede beneficiar o perjudicar que no le de bola a cambiar el kernel?

---

### Post by guillermolisi on 2010-09-04
La diferencia mas significativa entre el kernel generic y el RT (RealTime) esta en su latencia, es decir, de que forma administra los procesos que corren en la maquina.

Groseramente:

Generic no es ejecucion en tiempo real, entonces corre un rato cada proceso sin importar si aun no termino el que va a suspender para atender a otro. Es decir, reparte rodajas de tiempo de ejecucion por igual a los procesos que requieran atencion del kernel.

RealTime atiende un proceso y no lo suspende hasta que termina, dejando en espera a los demas que no esten relacionados con el primero. Como la ejecucion de musica, controladores MIDI por ejemplo, se realiza en tiempo real, por eso se utiliza este kernel.

---

### Post by joseluis on 2010-09-04
excelente explicación guillermo. Lo entendí perfectamente. Además busqué en wikipedia y me completó mas aún.
Gracias... me quedo con este kernel y cuento que actualicé a 10.10 beta. En otros post cuento a ver qué me pasa.

---

