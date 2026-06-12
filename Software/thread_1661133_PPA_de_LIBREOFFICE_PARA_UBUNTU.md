---
title: "PPA de LIBREOFFICE PARA UBUNTU"
date: 2011-01-06
forum: Software
---

### Post by Cajuma on 2011-01-06
Para quienes quieran ir probando Libbreoffice 3.3 rc2, ya esta 
disponible el PPA para Ubuntu 10.04,10.10 y 11.04.

Previo a la instalación hay que desinstalar Open Office:

```
sudo apt-get purge openoffice*.*
```

Añadir el PPA e instalar la aplicación:

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get install libreoffice
```

Puede que te tire un error al no encontrar algún paquete
(a mi me paso...)
En ese caso ejecutas:

```
Sudo apt-get install libreoffice --fix-missing
```

Para que no quede feo con ganas instalas:

Si usas Gnome:

```
sudo apt-get install libreoffice-gnome
```

Si usas Kde:

```
sudo apt-get install libreoffice-kde
```


Después instalas los paquetes de idioma diccionario y ayuda:

```
sudo apt-get install libreoffice-l10n-es
sudo apt-get install language-support-writing-es
sudo apt-get install libreoffice-help-es
```

Probado y funcionando.
Espero les sirva. ):P

---

### Post by rojojuan on 2011-01-06
Comparado con OpenOffice, que tal anda?

> **Cajuma said:**
> Para quienes quieran ir probando Libbreoffice 3.3 rc2, ya esta 
disponible el PPA para Ubuntu 10.04,10.10 y 11.04.

Previo a la instalación hay que desinstalar Open Office:

```
sudo apt-get purge openoffice*.*
```

Añadir el PPA e instalar la aplicación:

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get install libreoffice
```

Puede que te tire un error al no encontrar algún paquete
(a mi me paso...)
En ese caso ejecutas:

```
Sudo apt-get install libreoffice --fix-missing
```

Para que no quede feo con ganas instalas:

Si usas Gnome:

```
sudo apt-get install libreoffice-gnome
```

Si usas Kde:

```
sudo apt-get install libreoffice-kde
```


Después instalas los paquetes de idioma diccionario y ayuda:

```
sudo apt-get install libreoffice-l10n-es
sudo apt-get install language-support-writing-es
sudo apt-get install libreoffice-help-es
```

Probado y funcionando.
Espero les sirva. ):P

---

### Post by Cajuma on 2011-01-06
Lo instale en Maverick y hasta ahora todo bien, inclusive me
parece que anda mas rápido, y hasta podes instalarle las
extensiones de O.O., para el usuario normal de hojas de calculo
procesador de texto, y presentaciones, sobra.
Saludos :smile:

---

### Post by rojojuan on 2011-01-11
Muchas gracias por la respuesta. En poco tiempo más sale la versión definitiva.

> **Cajuma said:**
> Lo instale en Maverick y hasta ahora todo bien, inclusive me
parece que anda mas rápido, y hasta podes instalarle las
extensiones de O.O., para el usuario normal de hojas de calculo
procesador de texto, y presentaciones, sobra.
Saludos :smile:

---

### Post by gmunioz on 2011-01-25
Liberada la version final estable 3.3

Paquetes a descargar para Ubuntu

Version Final 3.3

Paquetes 32 bits

[http://download.documentfoundation.org/libreoffice/stable/3.3.0/deb/x86/LibO_3.3.0_Linux_x86_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/stable/3.3.0/deb/x86/LibO_3.3.0_Linux_x86_install-deb_en-US.tar.gz)

[http://download.documentfoundation.org/libreoffice/stable/3.3.0/deb/x86/LibO_3.3.0_Linux_x86_langpack-deb_es.tar.gz](http://download.documentfoundation.org/libreoffice/stable/3.3.0/deb/x86/LibO_3.3.0_Linux_x86_langpack-deb_es.tar.gz)

[http://download.documentfoundation.org/libreoffice/stable/3.3.0/deb/x86/LibO_3.3.0_Linux_x86_helppack-deb_es.tar.gz](http://download.documentfoundation.org/libreoffice/stable/3.3.0/deb/x86/LibO_3.3.0_Linux_x86_helppack-deb_es.tar.gz)

Paquetes 64 bits

[http://download.documentfoundation.org/libreoffice/stable/3.3.0/deb/x86_64/LibO_3.3.0_Linux_x86-64_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/stable/3.3.0/deb/x86_64/LibO_3.3.0_Linux_x86-64_install-deb_en-US.tar.gz)

[http://download.documentfoundation.org/libreoffice/stable/3.3.0/deb/x86_64/LibO_3.3.0_Linux_x86-64_langpack-deb_es.tar.gz](http://download.documentfoundation.org/libreoffice/stable/3.3.0/deb/x86_64/LibO_3.3.0_Linux_x86-64_langpack-deb_es.tar.gz)

[http://download.documentfoundation.org/libreoffice/stable/3.3.0/deb/x86_64/LibO_3.3.0_Linux_x86-64_helppack-deb_es.tar.gz](http://download.documentfoundation.org/libreoffice/stable/3.3.0/deb/x86_64/LibO_3.3.0_Linux_x86-64_helppack-deb_es.tar.gz)

Desde los repositorios (por ahora solo rc4)

En una terminal ejecutar:

sudo su
add-apt-repository ppa:libreoffice/ppa
apt-get update
apt-get install libreoffice libreoffice-gnome libreoffice-l10n-es libreoffice-l10n-common libreoffice-help-es language-support-writing-es

---

### Post by drazhe on 2011-01-26
> Alguien tiene idea cuando ponen la versión final estable en los repositorios de **Ubuntu**? recién me la instalé siguiendo los pasos mencionados arriba, pero instaló la versión RC4....

Pues, hoy se me actualizó el sistema y la versión RC4 de **LibreOffice** que había instalado, pasó a ser la versión final.. 
Lo único que puedo destacar es que tardó una eternidad de descargar 140mb de información... no se si será un problema de los servidores argentinos nuevamente o hay muchísima gente bajando lo mismo al mismo tiempo...

---

### Post by rojojuan on 2011-01-31
Instalé la versión final 3.3 y anda muy bien.

---

