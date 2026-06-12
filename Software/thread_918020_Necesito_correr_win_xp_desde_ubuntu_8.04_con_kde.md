---
title: "Necesito correr win xp desde ubuntu 8.04 con kde"
date: 2008-09-12
forum: Software
---

### Post by tuliobalcaldi on 2008-09-12
Hola, que tal? Estoy necesitando correr desde mi maquina, en la cual tengo exclusivamente ubuntu 8.04, un windows xp. Estuve leyendo por los foros y me decidi a instalar vmware, la cual se instalo correctamente pero no puedo ejecutarla. 
Luego leyendo aca vi que existe un sistema denominado virtualbox que corre mucho mas rapido que vmware y que tiene demas ventajas como ser libre (por lo que entendi). Lo que realmente no se es como instalarla (de donde la descargo? de los repositorios o desde terminal?) y despues como hacer para que me detecte el sistema operativo (si tengo que hacer una iso, etc).
La idea es meterla en mi compu, una dell latitude d630 (centrino core 2 duo 2 ghz, 1gb ram, disco 80gb, etc). Calculo que con los requerimientos no voy a tener problemas en si, mas uqe nada porque los programas que voy a usar tampoco necesitan grandes recursos (sony soundforge, sony vegas, etc).

Desde ya mcuhas gracias, saludos!

---

### Post by sajnox on 2008-09-12
Para Ubuntu 8.04 aca tenes la pagina con los repositorios

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Basicamente tenes que hacer lo siguiente

1) Agregar los repositorios

```
sudo kate /etc/apt/sources.list
```

y al final del archivo agregas lo siguiente

```
#Repositorios de Virtual Box
deb http://download.virtualbox.org/virtualbox/debian hardy non-free

```

2) Agregar la llave publica para que te permita la instalacion

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

```

3) Actualizas los repositorios

```
sudo apt-get update
```

4) Instalar virtual box

```
sudo aptitude install virtualbox
```

En Aplicaciones>Herramientas esta el acceso de virtual box

Ojo, vas a necesitar agregar tu usuario al grupo de vboxusers sino, no va andar

---

### Post by tuliobalcaldi on 2008-09-12
Joya! Mil gracias, hasta ahora quedo clarisimo, voy a probar entonces.
Una duda: el usuario mio lo agrego desde herramientas -> virtualbox luego de ser instalado o en algun paso intermedio?

---

### Post by sajnox on 2008-09-13
Es lo mismo que lo agregues antes o despues, si o si te lo exige para arrancar una maquina virtual. Antes ni te lo pregunta

Saludos

---

### Post by tuliobalcaldi on 2008-09-17
Barbaro! Muchas gracias, pude correrla perfectamente.
Tengo un solo inconveniente: como puedo usar el usb? No me lo toma de ninguna forma, pese a que active en la ventana de la maquina virtual las tres opciones de usb que figuran en el iconito de abajo a la derecha

---

### Post by sajnox on 2008-09-17
Muchas personas tuvieron el mismo problema, la solucion practica es agregar como directorio compartido el directorio donde monta el usb.

Siempre y cuando lo que quieras usar es un pendrive o similar, si es un hard ya no se bien que opciones tenes

---

### Post by guillermolisi on 2008-09-19
> **sajnox said:**
> Muchas personas tuvieron el mismo problema, la solucion practica es agregar como directorio compartido el directorio donde monta el usb.

Siempre y cuando lo que quieras usar es un pendrive o similar, si es un hard ya no se bien que opciones tenes

La version no libre de VBox permite mapear USB sin tener que hacer rodeos o utilizar Shared Folders para acceder.

---

### Post by tuliobalcaldi on 2008-09-22
Como sería eso de "mapear"? No entiendo la verdad, soy medio duro para este asunto como se podra ver.
Vi que abajo en la ventana de vbox hay una opcion grafica del usb y puedo activar las tres opciones que aparecen, los detecta windows pero no se instala y me dice que hay un problema en el hardware. Vale aclarar que solamente voy a utilizar pendrives.
=/

---

### Post by sajnox on 2008-09-22
En virtual box tenes la opcion de setear directorios compartidos en la configuracion del equipo y te pide que le asignes un nombre

Luego en la maquina virtual seguro que tenes montado en la unidad de cdrom (virtual) una .iso de vboxasittions (o algo asi se llama), lo abris y lo instalas (reinicias, como si hiciera falta...pero bueno, no todo es Linux)

Una vez instalado y reiniciado abris una terminal del SO virtualizado y escribis:

net use x: \\"nombre que diste al compartido"

Listo, te monto la unidad X el directorio compartido

---

### Post by tuliobalcaldi on 2008-09-22
Disculpa mi ignorancia, pero la verdad no logro entender.
Desde la ventana en la cual se virtualiza XP, en el menu Dispositivos -> directorios compartidos, en la opcion "directorios de la maquina" agregue uno llamado "Compartida", la cual se creo en el directorio de mi usuario (/home/tulio/Compartida). 
En la maquina virtual no tengo ninguna unidad de cd virtual, me sale "teac cdrom etc etc" que es la grabadora, por eso no entiendo bien que es lo que tengo que instalar.
Disculpa por mi ignorancia! Y mil gracias por la paciencia.
Saludos

---

### Post by sajnox on 2008-09-22
Nadie nacio sabiendo,menos a usar computadoras

En vbox en configuracion de maquina virtual, tomas la opcion de cd/dvd y elegis archivo .iso en lugar de la lectora real, y elegis la iso de vbox additions

Cuando inicias la maquina virtual, vas a tener en D: un archivo para ejecutar, eso le instala a windows las aplicaciones para compartir

Espero haber sido claro, sino vemos como lo explico mejor

---

### Post by sajnox on 2008-09-22
Te agrego un screenshot

---

### Post by tuliobalcaldi on 2008-09-23
Hasta ahora mas claro que el agua! Cargue la imagen perfectamente, instale sin problemas los archivos de la .iso y reinicie.
Lo que si el "net use x:\\" lo pongo en una ventana de dos via "cmd" en el menu ejecutar. Al poner "net use x:\\compartida" me sale "Error 67 - no se encuentra el nombre de red especificado".
La carpeta la cree en /home/tulio y la denomine Compartida, y la misma la cargue en Dispositivos -> directorios compartidos de la ventana correspondiente al sistema operativo.

---

### Post by sajnox on 2008-09-23
Desde la ventana de DOS escribi

net use x: \\vboxsvr\Compartida

Eso deberia andar

---

### Post by tuliobalcaldi on 2008-09-23
Sin palabras... mil gracias!! Anda genial ahora

Saludos! Y muchas gracias por la paciencia:)

---

