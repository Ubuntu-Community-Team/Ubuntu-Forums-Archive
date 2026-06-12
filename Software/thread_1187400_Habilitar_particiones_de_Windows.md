---
title: "Habilitar particiones de Windows"
date: 2009-06-14
forum: Software
---

### Post by ParamDaya on 2009-06-14
[FONT=Georgia][SIZE=2][B]Estimados

Formatee mi PC e instale Ubuntu. Ahora bien, yo antes en Windows tenia una particion de 36GB aproximadamente. Mi disco duro originalmente es de 250GB.

En Ubuntu instale el GParted, y me detecta 3 espacios:

1- /dev/sda1 232.88GiB Sistema de archivos ext3, Estado Montada en/
2- /dev/sda2 8.29GiB Sistema de archivos extended, Estado Ocupado (al menos una particion logica esta montada)
    3-  /dev/sda5 8.29GiB Sistema de archivos linux-swap, Estado Activa

Notese que la 3 la hice con tabulacion porque en GParted me aparece como dentro de sda2.

Ahora mi pregunta, de la sda2 y la sda5, alguna de esas 2 son activables para usarlas como espacio adicional, como alguna particion? O son particiones creadas normalmente por el sistema y no se pueden tocar?

Otra cosa, esto significa que la particion de 36GB que estaba en Windows, se borro con la instalacion de Ubuntu?

Muchas gracias.[/B][/SIZE][/FONT]

---

### Post by Carlos C on 2009-06-14
Al parecer formateaste todo el disco duro y perdiste tu partición de Windows. Tu partición sda1 es una partición primaria en donde tienes instalado Ubuntu y tu partición sda2 corresponde a una partición extendida. Se pueden tener hasta 4 particiones primarias en una tabla de particiones. Cuando necesitas más debes crear una partición extendida. Una partición extendida funciona como una partición primaria en la que agrupas una serie de particiones lógicas. Por esta razón es que la primera partición lógica, al interior de una partición extendida, siempre se encuentra en sda5.
En tu caso sda5 está siendo utilizada como la partición swap, que es la memoria de intercambio. Esa partición la necesitas. Más información sobre el sistema de particiones puedes encontrarla acá:

[http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro](http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro)

---

### Post by ParamDaya on 2009-06-14
> **Carlos C said:**
> Al parecer formateaste todo el disco duro y perdiste tu partición de Windows. Tu partición sda1 es una partición primaria en donde tienes instalado Ubuntu y tu partición sda2 corresponde a una partición extendida. Se pueden tener hasta 4 particiones primarias en una tabla de particiones. Cuando necesitas más debes crear una partición extendida. Una partición extendida funciona como una partición primaria en la que agrupas una serie de particiones lógicas. Por esta razón es que la primera partición lógica, al interior de una partición extendida, siempre se encuentra en sda5.
En tu caso sda5 está siendo utilizada como la partición swap, que es la memoria de intercambio. Esa partición la necesitas. Más información sobre el sistema de particiones puedes encontrarla acá:

[http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro](http://www.guia-ubuntu.org/index.php?title=Particionar_el_disco_duro)

[FONT=Georgia][SIZE=2][B]Muchas gracias por la respuesta.

Que aplicacion entonces puedo usar en Ubuntu para recuperar datos formateados? Asi como el paralelo de Magic Recovery de Windows.

Gracias.[/B][/SIZE][/FONT]

---

### Post by moreback on 2009-06-15
mmmh creo que ya perdiste los datos, mejor busca tus respaldos.

---

### Post by Psycopatologic on 2009-06-24
Mmmm, a ver, segun eso deberia ser tu directorio / la primera, la segunda la montaste como Home? y la tercera como swap?

De partida el directorio / esta en ext3 y es donde instalaste Ubuntu, la segunda no se que es pero esta formateada en formato extX y la tercera particion es el espacio Swap de linux, lo que tiene la misma funcion que el archivo de paginado de windows (se utiliza como buffer de datos). 

Por lo que leo ahi esta la totalidad del disco usado. Intenta entrando en Synaptic e instalando un paquete que se llama ntfs-3g config, al hacerlo vas a Administracion y entras en el programa, su objetivo es detectar particiones NTFS de windows, si es que quedo volando por ahi.

Lo que sugiero es que si no te da resultado reinstales ubuntu pero asignando al menos 1 directorio / (donde instalas el sistema operativo) , 1 directorio como home (es donde se guardan todos los cachureos jaja) y 4 o 6 Gb de swap, no es necesario mas. 

Para / si eres fan de instalar programas dale unos 40 gb (teniendo en cuenta que la instalacion solo ocupa 3 Gb), para swap unos 6 Gb y para Home todo lo que quieras y que tomes los respaldos y te pongas a copiar. Si vas a instalar windows ademas sugiero instales windows y despues ubuntu SIN TOCAR LAS PARTICIONES DE WINDOWS y que en ubuntu uses ntfs-3g para montar particiones de windows y para windows tb existen drivers para montar particiones en formato ext.

Saludos

---

