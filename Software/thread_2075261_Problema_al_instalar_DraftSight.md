---
title: "Problema al instalar DraftSight"
date: 2012-10-23
forum: Software
---

### Post by Senger on 2012-10-23
Ayer intenté instalar éste programa y no pude. Lo hice siguiendo esta guia:
[http://www.atareao.es/ubuntu/software-para-tu-ubuntu/como-conseguir-instalar-draftsight-en-ubuntu-natty-64-bits/]("http://www.atareao.es/ubuntu/software-para-tu-ubuntu/como-conseguir-instalar-draftsight-en-ubuntu-natty-64-bits/")

Al terminar de instalarlo, abro el menu de inicio y cuando le doy click al icono, sencillamente no hace nada. :confused:

Hoy volví a hacer todo el proceso y me tiro lo siguiente la terminal:

[IMG]http://ubuntuone.com/2uhLPkVdGZdFIggFWCvIkF[/IMG]

¿Alguien sabe qué podrá ser? :)

---

### Post by juancarlospaco on 2012-10-23
Te podes bajar un .DEB de la pagina, es para 32bit, pero lo instalas igual en 64bit con:

dpkg -i --force-all draftsight.deb

(si no anda se borra facil como un paquete comun)

---

### Post by Senger on 2012-10-24
> **juancarlospaco said:**
> Te podes bajar un .DEB de la pagina, es para 32bit, pero lo instalas igual en 64bit con:

dpkg -i --force-all draftsight.deb

(si no anda se borra facil como un paquete comun)

Creo que es lo que yo hice... ¿No?

Acabo de probar abrir el paquete con el comando que me pasaste, pero me tira lo mismo al final...

---

### Post by guillermolisi on 2012-10-24
> **Senger said:**
> Creo que es lo que yo hice... ¿No?
...
No, por lo que mostraste ejecutado en consola, no es lo mismo, pero para ser mas concluyentes seria de ayuda que tambien muestres lo que aparecio en pantalla cuando probaste la alternativa que sugirio juancarlospaco.

---

### Post by Senger on 2012-10-25
Ok, pido disculpas y paciencia ya que soy medio neófito con todo esto. Fui criado en WinXP y hace un tiempito que me pase a Ubuntu. De a poco algo voy aprendiendo :)

Para ejecutar ese comando, fui a la carpeta donde esta el archivo ".deb" y lo ejecute como "sudo"... ¿Esta bien eso? 

Aca dejo todo completo lo que hice:

```
alf@alf-M68MT-S2:~$ ls
Descargas   Escritorio  Música          temporal    Vídeos
Documentos  Imágenes    Senger Efectos  Ubuntu One
alf@alf-M68MT-S2:~$ cd Descargas/
alf@alf-M68MT-S2:~/Descargas$ ls
downverter-32.deb  draftSight.deb
alf@alf-M68MT-S2:~/Descargas$ dpkg -i --force-all draftSight.deb
dpkg: error: la operación precisa acceso de lectura y escritura al área de estado de dpkg
alf@alf-M68MT-S2:~/Descargas$ sudo dpkg -i --force-all draftSight.deb
[sudo] password for alf: 
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libexpat1 (>= 2.0.1-4)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libglib2.0-0 (>= 2.22.3-0)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libpcre3 (>= 7.8-3)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libselinux1 (>= 2.0.85-2)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de zlib1g (>= 1:1.2.3.3.dfsg-13)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libc6 (>= 2.10.1-0)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libx11-6 (>= 2:1.2.2-1)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libxau6 (>= 1:1.0.4-2)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libxcomposite1 (>= 1:0.4.0-4)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libxcursor1 (>= 1:1.1.9-1build1)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libxdamage1 (>= 1:1.1.1-4)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libxdmcp6 (>= 1:1.0.2-3)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libxext6 (>= 2:1.0.99.1-0)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libxfixes3 (>= 1:4.0.3-2build1)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libxi6 (>= 2:1.2.1-2)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libxinerama1 (>= 2:1.0.3-2)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libxrandr2 (>= 2:1.3.0-2)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libxrender1 (>= 1:0.9.4-2)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libatk1.0-0 (>= 1.28.0-0)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libcairo2 (>= 1.8.8-2)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libdirectfb-extra (>= 1.2.7-2)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libfontconfig1 (>= 2.6.0-1)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libfreetype6 (>= 2.3.9-5)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libgtk2.0-0 (>= 2.18.3-1)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libpango1.0-0 (>= 1.26.0-1)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libpixman-1-0 (>= 0.14.0-1)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libpng12-0 (>= 1.2.37-1)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libxcb-render0 (>= 1.4-1)
dpkg: aviso: ¡descartando problema de predependencia!
dpkg: acerca de draftSight.deb que contiene dassault-systemes-draftsight:i386, problema de predependencia:
 dassault-systemes-draftsight:i386 predepende de libxcb1 (>= 1.4-1)
dpkg: aviso: ¡descartando problema de predependencia!
(Leyendo la base de datos ... 185935 ficheros o directorios instalados actualmente.)
Desempaquetando dassault-systemes-draftsight:i386 (de draftSight.deb) ...
access control disabled, clients can connect from any host
access control disabled, clients can connect from any host
/var/lib/dpkg/tmp.ci/ShowLicence: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
access control enabled, only authorized clients can connect
access control enabled, only authorized clients can connect
dpkg: error al procesar draftSight.deb (--install):
 el subproceso script pre-installation nuevo devolvió el código de salida de error 127
Se encontraron errores al procesar:
 draftSight.deb

```

Gracias por su ayuda!! :mrgreen:

---

### Post by juancarlospaco on 2012-10-25
> **Senger said:**
> Creo que es lo que yo hice... ¿No?


No, por lo ejecutado en consola, es distinto, 
tenes que instalar las dependencias del paquete previamente, 
por que dpkg no las descarga, aunque las anuncia, 
y si, devolvera mensajes de advertencia por que es otra arquitectura y dependencias (64bit),
... pero iniciara, con suerte y paciencia.


Te aviso por las dudas..., 
que AutoDesk creo un AutoCAD Web basado en Adobe Flash, 
no es Libre pero es Gratis, no requiere instalar nada,
confirmo que funciona en Linux, sirve pasar .DWG a .DXF,
.DXF lo abris con FreeCAD, Blender, o cualquier app Libre:

[https://www.autocadws.com](https://www.autocadws.com)

---

### Post by Senger on 2012-10-27
PROBLEMA RESUELTO!:guitar:

Segui estos pasos: [http://linuxaideddesign.blogspot.com.es/2012/03/draftsight-and-ubuntu-1204-lts-64bit.html]("http://linuxaideddesign.blogspot.com.es/2012/03/draftsight-and-ubuntu-1204-lts-64bit.html")

---

