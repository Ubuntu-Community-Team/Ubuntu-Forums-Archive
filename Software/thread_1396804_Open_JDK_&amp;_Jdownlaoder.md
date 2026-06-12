---
title: "Open JDK &amp; Jdownlaoder"
date: 2010-02-02
forum: Software
---

### Post by NickCis on 2010-02-02
Hoy abri el Jdownloader (hace mucho que no lo usaba), y note qe todas las letras se veian mal =S...
No entiendo por que es,,, tengo la ultima version de JD, y todo mi ubuntu 9.10 actualizado.

Adjunto foto.

Vercion de java:
```

newpc@newpc:~$ java -showversion
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Client VM (build 14.0-b16, mixed mode, sharing)

```

Alguna ayuda?.

P.D.: definitivamente debe ser algo del java, por que si quiero cerrar el Jdownloader, no puedo hacerlo como una ventana normal (desde la x), si no que tengo que terminar matando al proceso java.

Saludos y gracias :P
Edit: aprece qe me achica la foto cuando la subo por este foro y no se entiende, aca dejo otro link:
[[IMG]http://img535.imageshack.us/img535/8060/23322643.th.png[/IMG]](http://img535.imageshack.us/i/23322643.png/)

---

### Post by fmsismo on 2010-02-02
En el 2008 hice un tuto para instalar Jdownlaoder en mi blog 

[http://www.sismonda.com.ar/procedimientos/jdownloader-gestor-de-descargas](http://www.sismonda.com.ar/procedimientos/jdownloader-gestor-de-descargas)

Explica como instalar el java de SUN.

Podes poner el path absoluto en tu acceso directo para ejecutar el java de sun

"/usr/lib/jvm/java-6-sun/jre/bin/java"

Para ver cuales tenes disponibles en el sistema

update-alternatives --list java

Para cambiar el java por defecto

sudo update-alternatives --config java

---

### Post by NickCis on 2010-02-02
Lo solucione instalando el OpenJdk 7, desde su ppa ( [https://launchpad.net/~openjdk/+archive/ppa](https://launchpad.net/~openjdk/+archive/ppa) )

Que diferencias hay entre usar el Open Jdk y el de sun?.

Saludos.

---

### Post by fmsismo on 2010-02-03
La direfencia entre los distintos javas es las librerías que dejan disponibles a los desarrolladores, LA LICENCIA y la "marca".

OpenJK esta creciendo y progresando mucho, pero el java de SUN sigue siendo el estándar para las aplicaciones/implementaciones comerciales.   Es muy rápido.

---

