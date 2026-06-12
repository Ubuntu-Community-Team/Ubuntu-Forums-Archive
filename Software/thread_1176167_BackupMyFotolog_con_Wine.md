---
title: "BackupMyFotolog con Wine"
date: 2009-06-02
forum: Software
---

### Post by vtssrm on 2009-06-02
Quiero correr el programa BackupMyFotolog en mi Ubuntu 9.04 pero no puedo :(. Relato mi procedimiento...

sudo apt-get install wine

luego ejecute con un doble clic el archivo backupmyfotolog.msi, se instala sin inconvenientes, lo busco en el menu Wine/BackupMyFotolog, lo elijo con un clic, se muestra el programa pero al ingresar el nombre del Fotolog a respaldar y darle al botón Descargar, me aparece un mensaje que dice:

Error '429' en tiempo de ejecución :
El componente ActiveX no puede crear el objeto

y solo me da la opción del botón Aceptar, eso es todo, adjunto unas capturas de lo sucedido y la página del programa en cuestión:


[http://www.imaxenes.com/imagen/11ac40ww.png.html](http://www.imaxenes.com/imagen/11ac40ww.png.html)
[http://www.imaxenes.com/imagen/21as0997.png.html](http://www.imaxenes.com/imagen/21as0997.png.html)


[http://www.backupmyfotolog.com/](http://www.backupmyfotolog.com/)


Les agradecería mucho que me dieran una mano... :p

---

### Post by guillermolisi on 2009-06-02
> **vtssrm said:**
> Quiero correr el programa BackupMyFotolog en mi Ubuntu 9.04 pero no puedo :(. Relato mi procedimiento...

sudo apt-get install wine

luego ejecute con un doble clic el archivo backupmyfotolog.msi, se instala sin inconvenientes, lo busco en el menu Wine/BackupMyFotolog, lo elijo con un clic, se muestra el programa pero al ingresar el nombre del Fotolog a respaldar y darle al botón Descargar, me aparece un mensaje que dice:

Error '429' en tiempo de ejecución :
El componente ActiveX no puede crear el objeto

y solo me da la opción del botón Aceptar, eso es todo, adjunto unas capturas de lo sucedido y la página del programa en cuestión:


[http://www.imaxenes.com/imagen/11ac40ww.png.html](http://www.imaxenes.com/imagen/11ac40ww.png.html)
[http://www.imaxenes.com/imagen/21as0997.png.html](http://www.imaxenes.com/imagen/21as0997.png.html)


[http://www.backupmyfotolog.com/](http://www.backupmyfotolog.com/)


Les agradecería mucho que me dieran una mano... :p
En la base de aplicaciones de Wine no figura "BackupMyFotolog", no con ese nombre, asi que pareceria algo dificil determinar que grado de funcionalidad se podria lograr.

Por otra parte, que version de Wine estas usando ? La estable o la ultima en desarrollo ?

---

### Post by vtssrm on 2009-06-02
La versión 1.0.1 que trae Ubuntu 9.04 en sus repositorios. Me imagino que es la estable...

---

### Post by guillermolisi on 2009-06-02
> **vtssrm said:**
> La versión 1.0.1 que trae Ubuntu 9.04 en sus repositorios. Me imagino que es la estable...
De hecho lo es pero me anime y probe la que esta en desarrollo, la ultima disponible en el repositorio de Wine y me sorprendio las diferencis a la hora de probar programas para Windows.

Hasta ahora no tuve mayores problemas y lo que con la estbale andaba mas o menos, con la ultima funciona barbaro.

No se si sera una solucion a lo que intentas resolver, pero con probar (en este caso) no se pierde nada. Si no resulta, lo desinstalas y a otra cosa.

De todas formas, el tema ActiveX en Linux es todo una cuestion.

---

### Post by Patriciologico on 2009-06-02
De no funcionarte lo que te recomienda guillermolisi, prueba creando una maquina virtual con VirtualBox e instalas un Windows liviano, para correr todas esas aplicaciones necesarias que dan dolores de cabeza.

Saludos!

---

### Post by guillermolisi on 2009-06-02
> **Patriciologico said:**
> De no funcionarte lo que te recomienda guillermolisi, prueba creando una maquina virtual con VirtualBox e instalas un Windows liviano, para correr todas esas aplicaciones necesarias que dan dolores de cabeza.

Saludos!
Coincido totalmente y me parece que es "la solucion" a este tema.

---

### Post by waraltca on 2010-01-13
> **guillermolisi said:**
> Coincido totalmente y me parece que es "la solucion" a este tema.

Correcto!!
Y asi de paso de devuelves a windows!
Tengo el mismo problema pero me rehuso a utilizar VirtualBox o cualquiermaquina virtual para instalar mi aplicacion.

Mejor seguir investigando que alguien tiene q saber!

---

### Post by _ZeTa on 2010-01-18
haz probado usar crossover??
:popcorn:
saludos!

---

