---
title: "Problema con dependencias en Skype"
date: 2010-09-10
forum: Software
---

### Post by kornykyano on 2010-09-10
El problema es que no puedo ejecutar ni actualizar Skype, hace semanas lo estaba usando normalmente. No se realmente que puede ser, por eso recurro a ustedes, ya que he estado instalando y testeando varios programas (realmente un lio).

Tengo instalado Skype 2.1.0.47, en terminal dice:

```
Fatal: Cannot mix incompatible Qt libraries
```

que libqt debo eliminar?

y si quiero instalarlo desde los repositorios ([http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/)) dice:

```
Depende: libasound2 (>1.0.16) pero se va a instalar 1.0.15-3ubuntu4
  Depende: libgcc1 (>=1:4.3) pero se va a instalar 1:4.2.4-1ubuntu4
  Depende: libqt4-dbus (>=4.4.3) but it is not installable
  Depende: libqt4-network (>=4.4.3) pero se va a instalar 4.4.0-1ubuntu5~hardy1
  Depende: libqtcore4 (>=4.4.3) pero se va a instalar 4.4.0-1ubuntu5~hardy1
  Depende: libqtgui4 (>=4.4.3) pero se va a instalar 4.4.0-1ubuntu5~hardy1
  Depende: libstdc++6 (>=4.3) pero se va a instalar 4.2.4-1ubuntu4
  E: Paquetes rotos


```

En un foro vi que hay que hacer instalación forzada, mmm no se que opinan?
Yo sigo con ubuntu 8.04.4, lo tengo actualizar?

---

### Post by juancarlospaco on 2010-09-10
Las librerias son muy viejas para esa version de Skype...

---

### Post by kornykyano on 2010-09-10
Si, actualizarlo no creo que sea factible. Pero lo que tengo instalado debería ejecutarse, el tema es encontrar que es lo que esta molestando...

---

### Post by mama21mama on 2010-09-10
por que no lo bajas de la web oficial de skype?

[http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)

> mama@zeusa:~$ skype --version
Skype 2.1.0.81
Copyright (c) 2004-2009, Skype Limited
mama@zeusa:~$ 



---

### Post by kornykyano on 2010-09-11
Ya lo hice...y nada

---

### Post by mama21mama on 2010-09-11
Hola, prueba este metodo.

```
sudo apt-get install ia32-libs lib32asound2; wget -O skype-install.deb http://www.skype.com/go/getskype-linux-ubuntu; sudo dpkg -i --force-all skype-install.deb
```

[URL="http://ferarg.blogspot.com/2008/07/instalar-skype-en-ubuntu-804-hardy.html"]
Fuente[/URL]

---

### Post by kornykyano on 2010-09-12
> **mama21mama said:**
> Hola, prueba este metodo.
```
sudo apt-get install ia32-libs lib32asound2; wget -O skype-install.deb http://www.skype.com/go/getskype-linux-ubuntu; sudo dpkg -i --force-all skype-install.deb
```
[URL="http://ferarg.blogspot.com/2008/07/instalar-skype-en-ubuntu-804-hardy.html"]
Fuente[/URL]
esto es para 64bits, no 32bits.

---

### Post by josecuervo86 on 2010-09-12
Eso que te paso es para hecer una instalación forzada de skype 32 bits en una de 64 bits.
```
sudo dpkg -i --force-all skype-install.deb
```

Sacado del MAN de dpkg (man dpkg):
**-i:** Install  the  package (instala el paquete)
**--force:** Force to  do  some  things (fuerza a hacer algunas cosas)
**--force-all:** Turns on all force options ("fuerza todo")

Algunas veces es la unica que te queda, como para instalar el Adobe Reader, en otras por ahi no es necesario.

---

### Post by kornykyano on 2010-09-13
Creo que no me explique bien, yo no tengo 64bits.

El tema esta en que "libqt" debo eliminar para usar la versión 2.1.0.47. No creo que se pueda actualizar a la 2.1.0.81 ya que depende de varias librerias que a su vez depende de otros programas.

---

### Post by guillermolisi on 2010-09-13
Lo que te estan sugiriendo es que realices una instalacion forzada, mas alla del tema 32 y 64 bits que solo desvia el asunto. Lo importante es la opcion --force-all.

En el peor de los casos instalara y no funcionara con lo cual podes remover el paquete y buscar otra alternativa.

---

### Post by kornykyano on 2010-09-14
Ya lo pude arreglar aunque no es la última version (2.1.0.81). Tuve que hacer una actualización de hardy-proposed y hardy-backports:

> Actualizó los paquetes siguientes:
libqt4-core (4.3.4-0ubuntu3.1) to 4.4.0-1ubuntu5~hardy1
libqt4-gui (4.3.4-0ubuntu3.1) to 4.4.0-1ubuntu5~hardy1
libqt4-qt3support (4.3.4-0ubuntu3.1) to 4.4.0-1ubuntu5~hardy1
libqt4-sql (4.3.4-0ubuntu3.1) to 4.4.0-1ubuntu5~hardy1

Instaló los paquetes siguientes:
libqt4-assistant (4.4.0-1ubuntu5~hardy1)
libqt4-dbus (4.4.0-1ubuntu5~hardy1)
libqt4-designer (4.4.0-1ubuntu5~hardy1)
libqt4-network (4.4.0-1ubuntu5~hardy1)
libqt4-opengl (4.4.0-1ubuntu5~hardy1)
libqt4-script (4.4.0-1ubuntu5~hardy1)
libqt4-svg (4.4.0-1ubuntu5~hardy1)
libqt4-test (4.4.0-1ubuntu5~hardy1)
libqt4-xml (4.4.0-1ubuntu5~hardy1)

Lo raro que antes de esto también funcionaba, pero bue! la magia de Ubuntu ;) . La instalación forzada lo dejo para otro momento.

Gracias por su tiempo gente ...

---

