---
title: "Problemas con espacio libre"
date: 2009-06-10
forum: Software
---

### Post by M3's on 2009-06-10
Hola, es la primera vez que me ocurre este error, actualmente estoy utilizando jaunty, soy usuario de todas las versiones anteriores salvo 8.10 y mi problema se da en no poder utilizar el total del espacio libre disponible en particiones ntfs, con 8.04 lo podía hacer.
Acaso en esta versión tiene un espacio reservado como las particiones ext3?

---

### Post by guillermolisi on 2009-06-10
> **M3's said:**
> Hola, es la primera vez que me ocurre este error, actualmente estoy utilizando jaunty, soy usuario de todas las versiones anteriores salvo 8.10 y mi problema se da en no poder utilizar el total del espacio libre disponible en particiones ntfs, con 8.04 lo podía hacer.
Acaso en esta versión tiene un espacio reservado como las particiones ext3?
Como para poder entender mejor el contexto:

Es una maquina con dual boot y desde Ubuntu trabajas/accedes a la particion WIndows que esta en NTFS ?

Cuando te referis a "utilizar el total del espacio libre en particiones NTFS", a que te estas refiriendo, concretamente ? Por ahi con un ejemplo de como haces/usas ese espacio libre dara una idea mas acabada.

---

### Post by ADICTOALMAXIMO on 2009-06-11
Yo tengo particionado para guindows,linux y datos y puedo guardar hacer lo que quiera en esos 30 gb que le di a windows

---

### Post by rubioo on 2009-06-11
> **ADICTOALMAXIMO said:**
> Yo tengo particionado para guindows,linux y datos y puedo guardar hacer lo que quiera en esos 30 gb que le di a windows

 Yo tambien tengo los 2 sistemas, y desde ubuntu puedo leer/escribir en la
 partición de windows sin ningún problema. Pero no al revés.

---

### Post by M3's on 2009-06-20
Tengo dualboot y particionado el disco de la siguiente forma: 1 partición ntfs primaria con Windows, otra partición primaria ext3 con Ubuntu, una partición extendida ext3 con el Home, y otra extendida NTFS para datos en la cual vuelco generalmente contenidos de otros discos y realizo limpieza de virus, con varios antivirus (unica razón por la que continua instalado Windows). Esa última partición de 400 Gb en la cual me indica espacio disponible de 14 Gb no me permite continuar copiando archivos y me indica que no hay espacio disponible, cuando el archivo a copiar pesa menos de 600 mb.
Bootendo desde un backup realizado con remastersys de Ubuntu 8.04 no tengo problemas en continuar copiando archivos, por eso mi duda al respecto si Jaunty tiene un espacio de disco reservado en cualquier formato de partición

---

### Post by guillermolisi on 2009-06-20
> **M3's said:**
> Tengo dualboot y particionado el disco de la siguiente forma: 1 partición ntfs primaria con Windows, otra partición primaria ext3 con Ubuntu, una partición extendida ext3 con el Home, y otra extendida NTFS para datos en la cual vuelco generalmente contenidos de otros discos y realizo limpieza de virus, con varios antivirus (unica razón por la que continua instalado Windows). Esa última partición de 400 Gb en la cual me indica espacio disponible de 14 Gb no me permite continuar copiando archivos y me indica que no hay espacio disponible, cuando el archivo a copiar pesa menos de 600 mb.
Bootendo desde un backup realizado con remastersys de Ubuntu 8.04 no tengo problemas en continuar copiando archivos, por eso mi duda al respecto si Jaunty tiene un espacio de disco reservado en cualquier formato de partición
No, no hay una reserva de espacio especial de parte de Ubuntu mas alla de las particiones que se hagan en los discos al momento de instalar/particionar. Ahi hay otro problema, tal vez con la fragmentacion de la particion NTFS o con el utilitario necesario para acceder desde Ubuntu a particiones con ese tipo de filesystem.

Luego, me parece que el orden mas logico es que necesitas antivirus por consecuencia de tener windows, no al reves.

No hace falta Windows para correr antivirus y analizar archivos que despues usaras en maquinas con Windows. Los podes alojar en una particion EXT3 y correrles antivirus desde Linux directamente. Es mucho mas seguro, rapido y no tenes los problemas de fragmentacion que presenta NTFS (ademas de este problema particular de las diferencias de disponibilidad que mencionas).

---

### Post by M3's on 2009-06-20
Los datos que copio y limpio no son míos y la mayoría de los antivirus para GNU/Linux no suelen reparar archivos infectados sino que solo puedes eliminarlos, he probado correr Nod32 desde Ubuntu pero no lo he logrado, ya que este si repara archivos infectados con cierto tipo de gusano, además solo cuento con una licencia para Windows del mismo y la versión exitente para GNU/Linux es para servidores y nada económica.
Respecto a la fragmentación del volumen no es ya que desfragmenté y como dije anteriormente desde 8.04 y desde el mismo Windows puedo continuar copiando, respecto a algún problema con el paquete que administra soporte ntfs realicé una instalación nueva en un disco aparte e intenté continuar copiando datos en la partición del disco de la falla y aún me indica que no puede copiar el archivo por falta de espacio en disco.
Realmente con Jaunty he tenido varios problemas ya que no es sólo ésto sino otras fallas con la utilización de kdetv con una sintonizadora de tv (ni siquiera con Dapper Drake tuve ese conflicto y recuerdo haber tenido que recompilar el kernel para que me reconozca esa placa) y problemas de audio por culpa de pulse, espero no tener esos problemas  Karmic Koala, porque esta versión me ha dado más de un dolor de cabeza.
Igualmente gracias

---

### Post by WanderingKnight on 2009-06-20
Qué te tira df -h?

---

### Post by guillermolisi on 2009-06-20
> **M3's said:**
> Los datos que copio y limpio no son míos y la mayoría de los antivirus para GNU/Linux no suelen reparar archivos infectados sino que solo puedes eliminarlos, he probado correr Nod32 desde Ubuntu pero no lo he logrado, ya que este si repara archivos infectados con cierto tipo de gusano, además solo cuento con una licencia para Windows del mismo y la versión exitente para GNU/Linux es para servidores y nada económica.
Respecto a la fragmentación del volumen no es ya que desfragmenté y como dije anteriormente desde 8.04 y desde el mismo Windows puedo continuar copiando, respecto a algún problema con el paquete que administra soporte ntfs realicé una instalación nueva en un disco aparte e intenté continuar copiando datos en la partición del disco de la falla y aún me indica que no puede copiar el archivo por falta de espacio en disco.
Realmente con Jaunty he tenido varios problemas ya que no es sólo ésto sino otras fallas con la utilización de kdetv con una sintonizadora de tv (ni siquiera con Dapper Drake tuve ese conflicto y recuerdo haber tenido que recompilar el kernel para que me reconozca esa placa) y problemas de audio por culpa de pulse, espero no tener esos problemas  Karmic Koala, porque esta versión me ha dado más de un dolor de cabeza.
Igualmente gracias
Hay varias herramientas antivirus que hacen lo que vos haces con las de Windows.

TRK - Trinity Rescue Kit es una y corre hasta 5 antivurs distintos de los cuales 4 tienen capacidad de limpieza (AVG, F-Prot, BitDefender y Vexira Antivir).
Lo grabas en un CD, inicias la maquina con el y revisas todo sin excepcin con actualziacion al momento (via Internet).

Usa versiones de antivirus free, con lo cual con encontrar sus URLs alcanza para bajarte los paquetes que hagan falta y correrlos desde el disco en EXT3.

---

