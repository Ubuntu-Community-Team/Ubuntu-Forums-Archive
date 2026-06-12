---
title: "LibreOffice 4.0 en Ubuntu 10.04 (Lucid Lynx)"
date: 2013-02-07
forum: Software
---

### Post by drazhe on 2013-02-07
Hola, tengo instalado **LibreOffice 3x** en mi Lucid, lo cual había hecho a través del PPA, mi pregunta es si se va a actualizar a la versión 4 que acaba de salir o tengo que reinstalarlo por completo.

---

### Post by biale on 2013-02-08
El soporte para Lucid cae en abril de este año. O sea que es muy improbable que se llegue a la versión 4. Consultando un PPA solo encuentro paquetes 3.6 para Raring Ringtail.

---

### Post by drazhe on 2013-02-09
> **biale said:**
> El soporte para Lucid cae en abril de este año. O sea que es muy improbable que se llegue a la versión 4. Consultando un PPA solo encuentro paquetes 3.6 para Raring Ringtail.

Gracias por responder, se que tengo que tengo que actualizar, pasa que funciona tan bien Lucid y me incomoda tanto unity que estoy estirando la actualización lo más que se pueda jejeje

Pero preguntaba solo por curiosidad, eventualmente no voy a tener alternativa de pasarme a la siguiente LTS... 

Saludos y nuevamente gracias por responder...

---

### Post by guillermolisi on 2013-02-11
Veo un nuevo escritorio grafico en tu futuro :)

---

### Post by gmunioz on 2013-02-11
¿Y por qué no instalas los paquetes bajados desde su sitio?
32 bits
[http://download.documentfoundation.org/libreoffice/stable/4.0.0/deb/x86/LibreOffice_4.0.0_Linux_x86_deb.tar.gz](http://download.documentfoundation.org/libreoffice/stable/4.0.0/deb/x86/LibreOffice_4.0.0_Linux_x86_deb.tar.gz)
[http://download.documentfoundation.org/libreoffice/stable/4.0.0/deb/x86/LibreOffice_4.0.0_Linux_x86_deb_langpack_es.tar.gz](http://download.documentfoundation.org/libreoffice/stable/4.0.0/deb/x86/LibreOffice_4.0.0_Linux_x86_deb_langpack_es.tar.gz)
[http://download.documentfoundation.org/libreoffice/stable/4.0.0/deb/x86/LibreOffice_4.0.0_Linux_x86_deb_helppack_es.tar.gz.mirrorlist](http://download.documentfoundation.org/libreoffice/stable/4.0.0/deb/x86/LibreOffice_4.0.0_Linux_x86_deb_helppack_es.tar.gz.mirrorlist)

64 bits
[http://download.documentfoundation.org/libreoffice/stable/4.0.0/deb/x86_64/LibreOffice_4.0.0_Linux_x86-64_deb.tar.gz](http://download.documentfoundation.org/libreoffice/stable/4.0.0/deb/x86_64/LibreOffice_4.0.0_Linux_x86-64_deb.tar.gz)
[http://download.documentfoundation.org/libreoffice/stable/4.0.0/deb/x86_64/LibreOffice_4.0.0_Linux_x86-64_deb_langpack_es.tar.gz](http://download.documentfoundation.org/libreoffice/stable/4.0.0/deb/x86_64/LibreOffice_4.0.0_Linux_x86-64_deb_langpack_es.tar.gz)
[http://download.documentfoundation.org/libreoffice/stable/4.0.0/deb/x86_64/LibreOffice_4.0.0_Linux_x86-64_deb_helppack_es.tar.gz](http://download.documentfoundation.org/libreoffice/stable/4.0.0/deb/x86_64/LibreOffice_4.0.0_Linux_x86-64_deb_helppack_es.tar.gz)

Descomprimes los archivos, colocas todos los archivos.deb en un mismo directorio y lo instalas con
sudo su
dpkg -i *.deb

Previamente es necesario desinstalar las versiones previas de libreoffice y openoffice.

---

### Post by EnriqueK on 2013-02-11
Por suerte los principales programas permiten ser actualizados desde su sitio oficial, no solo  se puede desde repositorios, por eso recomiemdo que sigas em la 10. 04 , las nuevas versiones son simplemente inaceptables.
El caso mas curioso es  el de Red Hat, esa empresa está detrás de Gmome y de Fedora, sin embargo, su producto comercial o  sea el RHel  trae por defeccto Gnome 2, esto se puede comprobar descargando Centos que es un Fork del RHeL  y que sigue sus pasos al día ,  te vas  a arrepentir si actualizas a la 12.04

---

### Post by biale on 2013-02-11
Parece que somos varios los que seguimos con Lucid...

Yo en cambio prefiero tocar lo menos posible. En caso de actualizar por una via que no sean los repositorios y si la maquina ademas esta en produccion sugiero un backup de las areas de sistema. 

> las nuevas versiones son simplemente inaceptables

Interesante, observo que una buena parte del mundo Linux esta tratando de estirar Gnome 2 hasta donde se pueda.

---

### Post by wolferl on 2013-02-12
Uno más que sigue con 10.04...y en mi caso con la Netbook Edition :D

También me gustaría poder instalar Libreoffice 4, pero prefiero los repositorios si es posible.

---

### Post by jrierab on 2013-07-16
Por si alguien llega tarde al hilo, como yo, ya existe un PPA : [https://launchpad.net/~libreoffice/+archive/libreoffice-4-0](https://launchpad.net/~libreoffice/+archive/libreoffice-4-0).

---

