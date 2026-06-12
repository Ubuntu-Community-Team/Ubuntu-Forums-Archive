---
title: "Empezando Con Ubuntu"
date: 2010-02-24
forum: Software
---

### Post by ruidodemente on 2010-02-24
Hola a todos estoy empezando mis primeros pasos con Ubuntu cansado ya un poco de Windows. Soy de San Miguel Bs As Argentina - Me dedico al diseño web y desarrollo y bla bla bla.

Al empezar con linux me encontre con una duda y es basicamente el tema de las particiones si bien tengo Windows 7 en mi Pc instale el Ubuntu 9 lo cual aparentemente fue bien pero a la hora de descargar actualizaciones me dice que no tengo espacio. Alguin me podria guiar con el tema de las particiones y que funcion cumplen es para poder entender el funcionamiento y asi crear mis propias particiones.

Tengo un Disco de 160 particionado en 2 en una de las particiones ya tengo instalado Win y quiesiera saber las opciones que tengo a la hora de instalar ya que no me quedo muy clara la explicacion del instalador. 

por ejemplo?
* Es posible instalar linux en la misma particion de windows
* cuanto espacio debo dejarle a linux (por favor detallenme el formato de particion)


Gracias espero que se entienda el mensaje:P

---

### Post by atari130xe on 2010-02-24
> **ruidodemente said:**
> Hola a todos estoy empezando mis primeros pasos con Ubuntu cansado ya un poco de Windows. Soy de San Miguel Bs As Argentina - Me dedico al diseño web y desarrollo y bla bla bla.

Al empezar con linux me encontre con una duda y es basicamente el tema de las particiones si bien tengo Windows 7 en mi Pc instale el Ubuntu 9 lo cual aparentemente fue bien pero a la hora de descargar actualizaciones me dice que no tengo espacio. Alguin me podria guiar con el tema de las particiones y que funcion cumplen es para poder entender el funcionamiento y asi crear mis propias particiones.

Tengo un Disco de 160 particionado en 2 en una de las particiones ya tengo instalado Win y quiesiera saber las opciones que tengo a la hora de instalar ya que no me quedo muy clara la explicacion del instalador. 

por ejemplo?
* Es posible instalar linux en la misma particion de windows
* cuanto espacio debo dejarle a linux (por favor detallenme el formato de particion)


Gracias espero que se entienda el mensaje:P

Hola como estás? el tema de las particiones normalmente se manejan antes de instalar el Sistema operativo para que luego no ocurran este tipo de inconvenientes. Si usás un dual boot con Win como es tu caso y disponés por ej de un Disco de 160GB, yo dejaría 80 y 80 si utilizo los 2 por igual, ahora si utilizás más Ubuntu entonces dejaría la particion de Win mas pequeña. Las que yo utilizo normalmente en mis instalaciones dual boot son asi: una partición de 70 o 75 Gigas para Win, luego otra particion para "/" que es el directorio raíz donde se instala el sistema en sí de unos 15GB (puede ser un poco más si sabés que vas a instalar muchos programas), otra partición "/home" que es donde van a ir todos mis archivos (es como "mis documentos" en win) con lo que queda de espacio en el disco y reservo espacio 1GB para la swap (particion de intercambio para la memoria) es maso lo que hago en mis instalaciones Dual boot, aunque últimamente estoy haciendo instalaciones con Ubuntu únicamente por pedido de mis conocidos y amigos porque se animan a aprender Linux.

Te quedaría algo así:
Windows (partición primaria)
Ubuntu "/" (particion primaria)
Ubuntu "/Home" (partición primaria)
Ubuntu "swap" (partición primaria)

Solo podés tenér hasta 4 particiones primarias luego de eso tenés que crear extendidas. Gparted hace todo ese trabajo, es intuitivo y de alguna manera "entendible".

---

### Post by luks911 on 2010-02-24
> **ruidodemente said:**
> Hola a todos estoy empezando mis primeros pasos con Ubuntu cansado ya un poco de Windows. Soy de San Miguel Bs As Argentina - Me dedico al diseño web y desarrollo y bla bla bla.
Bienvenido

> **ruidodemente said:**
> Al empezar con linux me encontre con una duda y es basicamente el tema de las particiones si bien tengo Windows 7 en mi Pc instale el Ubuntu 9 lo cual aparentemente fue bien pero a la hora de descargar actualizaciones me dice que no tengo espacio. Alguin me podria guiar con el tema de las particiones y que funcion cumplen es para poder entender el funcionamiento y asi crear mis propias particiones.
Primero un par de preguntas: ¿Instalaste Ubuntu de la forma "normal" iniciando la PC desde el CD o lo instalaste desde Windows usando Wubi? Creo que es la primera, pero para estar seguro.
Después, abrí una terminal (Aplicaciones > Accesorios > Terminal) y ejecutá el comando
```
df -m
``` tipeas eso, das enter, y copiá y pegá acá lo que te devuelve. Eso muestra las particiones que tenés y qué porcentaje tienen con datos.
Las particiones son, dicho muy simple (no me pidan más), espacios en los que se divide el disco rígido para organizar la información. 

> **ruidodemente said:**
> 
Tengo un Disco de 160 particionado en 2 en una de las particiones ya tengo instalado Win y quiesiera saber las opciones que tengo a la hora de instalar ya que no me quedo muy clara la explicacion del instalador. 

por ejemplo?
* Es posible instalar linux en la misma particion de windows
* cuanto espacio debo dejarle a linux (por favor detallenme el formato de particion)


Gracias espero que se entienda el mensaje:P

Las opciones que te da el instalador son en principio 3 y tal vez no en el orden que las detallo:
1) Instalar encima de Windows. Es decir eliminarlo y en esa partición poner Ubuntu. No es lo que querés si buscás mantener los dos sistemas. E incluso no es lo mejor si sólo querés instalar Ubuntu.
2) Instalar Ubuntu junto a Windows con particionado automático. Se mantienen ambos sistemas y al iniciar elegís cuál usar, se llama dual-boot. El instalador divide el disco en dos y crea una nueva partición para Ubuntu (con el sistema de archivos ext4) y otra para el Swap (es el área de intercambio, una especie de ayuda para la memoria RAM que necesitan los sistemas GNU/Linux y que tendrá entre 512MB y 1GB).
3) Particionado manual. Con esta opción elegis qué particiones crear y qué tamaño les das. Así vas a reducir el tamaño de la de Windows (es importante que antes de iniciar esta instalación desfragmentes tu Win) y en el espacio libre vas crear las particiones para Ubuntu. Una partición / (es donde van los archivos del sistema) en ext4 y con 20GB está más que bien; otra partición /home (es donde van tus documentos y configuraciones de programas) también en ext4 y, si dividiste el disco en 2, con 59GB, y una partición Swap o Área de intercambio de 1GB. Tener separados el sistema (/) de tus archivos (/home) te permite reinstalar (por actualizaciones de versión, por ejemplo) sin perder tus datos ni configuraciones.
Te dejo un link[0] a un tutorial de instalación donde vas a poder ver cómo es el particionado manual. Ahí no hay un Win, es de una versión viejita de Ubuntu y se usa ext3 en lugar de ext4, pero el procedimiento de editar las particiones es idéntico.

[0] [http://www.fentlinux.com/web/?q=node/2408](http://www.fentlinux.com/web/?q=node/2408)

---

