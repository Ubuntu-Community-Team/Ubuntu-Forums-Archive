---
title: "Usando Zeitgeist y GNOME Activity Journal"
date: 2010-01-14
forum: Software
---

### Post by CdK1 on 2010-01-14
Instalación de Zeitgeist y GNOME Activity Journal.-

 1.- Qué es Zeitgeist y GNOME Activity Journal?

 Zeitgeist y GNOME Activity Journal son una de las tantas maravillas que traerá Gnome 3, básicamente consiste en una utilidad/herramienta que nos permitirá/ayudará a encontrar archivos en nuestro equipo de una manera bastante &#8220;novedosa&#8221;, ya que está enfocado a búsquedas según:
 
 Tipo de datos
Fuente
Tiempo
Nombre
Etiquetas (Tags)
Archivos similares
Comentarios
Localizacion de uso(GPS)
 
2.- Preparando el sistema:
 
Caturra:/# apt-get update
Obj [http://debian.utalca.cl](http://debian.utalca.cl) sid Release.gpg
Obj [http://debian.utalca.cl](http://debian.utalca.cl) sid/main Translation-es
Obj [http://debian.utalca.cl](http://debian.utalca.cl) unstable Release.gpg
#############################################
Ign [http://www.lamaresh.net](http://www.lamaresh.net) sid/main Packages
Ign [http://www.lamaresh.net](http://www.lamaresh.net) sid/main Packages
Obj [http://www.lamaresh.net](http://www.lamaresh.net) sid/main Packages
Descargados 3643B en 4s (877B/s)
Leyendo lista de paquetes&#8230; Hecho
Caturra:/# apt-get dist-upgrade
Leyendo lista de paquetes&#8230; Hecho
Creando árbol de dependencias
Leyendo la información de estado&#8230; Hecho
Calculando la actualización&#8230; Listo
Los siguientes paquetes se han retenido:
  grub
0 actualizados, 0 se instalarán, 0 para eliminar y 1 no actualizados.
Caturra:/# apt-get upgrade
Leyendo lista de paquetes&#8230; Hecho
Creando árbol de dependencias
Leyendo la información de estado&#8230; Hecho
Los siguientes paquetes se han retenido:
  grub
0 actualizados, 0 se instalarán, 0 para eliminar y 1 no actualizados.
Caturra:/# 
 
2.- Instalamos lo necesario:
 
Caturra:/# apt-get install bzr gnome-common
Leyendo lista de paquetes&#8230; Hecho
Creando árbol de dependencias
Leyendo la información de estado&#8230; Hecho
Se instalarán los siguientes paquetes extras:
  autoconf automake autotools-dev gettext intltool libtool m4
Paquetes sugeridos:
autoconf2.13 autoconf-archive gnu-standards autoconf-doc bzr-gtk bzr-svn python-pycurl python-kerberos bzr-doc gettext-doc libtool-doc automaken gfortran
  fortran95-compiler gcj
Paquetes recomendados
  bzrtools python-paramiko cvs libltdl-dev
Se instalarán los siguientes paquetes NUEVOS:
  autoconf automake autotools-dev bzr gettext gnome-common intltool libtool m4
0 actualizados, 9 se instalarán, 0 para eliminar y 1 no actualizados.
Se necesita descargar 4883kB/7822kB de archivos.
Se utilizarán 29,3MB de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]?
Des:1 [http://debian.utalca.cl](http://debian.utalca.cl) sid/main m4 1.4.13-3 [241kB]
Des:2 [http://debian.utalca.cl](http://debian.utalca.cl) sid/main autoconf 2.65-3 [772kB]
Des:3 [http://debian.utalca.cl](http://debian.utalca.cl) sid/main autotools-dev 20090611.1 [64,1kB]
Des:4 [http://debian.utalca.cl](http://debian.utalca.cl) sid/main automake 1:1.11-1 [620kB]
Des:5 [http://debian.utalca.cl](http://debian.utalca.cl) sid/main gettext 0.17-8 [2433kB]
Des:6 [http://debian.utalca.cl](http://debian.utalca.cl) sid/main libtool 2.2.6b-2 [526kB]
Des:7 [http://debian.utalca.cl](http://debian.utalca.cl) sid/main intltool 0.40.6-2 [102kB]
Des:8 [http://debian.utalca.cl](http://debian.utalca.cl) sid/main gnome-common 2.28.0-1 [124kB]
Descargados 4883kB en 20s (243kB/s)
Seleccionando el paquete m4 previamente no seleccionado.
(Leyendo la base de datos &#8230;  00%
129615 ficheros y directorios instalados actualmente.)
Desempaquetando m4 (de &#8230;/archives/m4_1.4.13-3_i386.deb) &#8230;
Seleccionando el paquete autoconf previamente no seleccionado.
Desempaquetando autoconf (de &#8230;/autoconf_2.65-3_all.deb) &#8230;
Seleccionando el paquete autotools-dev previamente no seleccionado.
Desempaquetando autotools-dev (de &#8230;/autotools-dev_20090611.1_all.deb) &#8230;
Seleccionando el paquete automake previamente no seleccionado.
Desempaquetando automake (de &#8230;/automake_1%3a1.11-1_all.deb) &#8230;
Seleccionando el paquete bzr previamente no seleccionado.
Desempaquetando bzr (de &#8230;/archives/bzr_2.0.3-1_i386.deb) &#8230;
Seleccionando el paquete gettext previamente no seleccionado.
Desempaquetando gettext (de &#8230;/gettext_0.17-8_i386.deb) &#8230;
Seleccionando el paquete libtool previamente no seleccionado.
Desempaquetando libtool (de &#8230;/libtool_2.2.6b-2_i386.deb) &#8230;
Seleccionando el paquete intltool previamente no seleccionado.
Desempaquetando intltool (de &#8230;/intltool_0.40.6-2_all.deb) &#8230;
Seleccionando el paquete gnome-common previamente no seleccionado.
Desempaquetando gnome-common (de &#8230;/gnome-common_2.28.0-1_all.deb) &#8230;
Procesando disparadores para install-info &#8230;
Procesando disparadores para man-db &#8230;
Configurando m4 (1.4.13-3) &#8230;
Configurando autoconf (2.65-3) &#8230;
Configurando autotools-dev (20090611.1) &#8230;
Configurando automake (1:1.11-1) &#8230;
update-alternatives: using /usr/bin/automake-1.11 to provide /usr/bin/automake (automake) in auto mode.
Configurando bzr (2.0.3-1) &#8230;
Configurando gettext (0.17-8) &#8230;
Configurando libtool (2.2.6b-2) &#8230;
Configurando intltool (0.40.6-2) &#8230;
Configurando gnome-common (2.28.0-1) &#8230;
 Caturra:/#

 Estamos listos&#8230;
 
3.- Bajando e instalando Zeitgeist.-
 
La verdad es que puede ser en cualquier directorio, lo elegí /usr/local/src/ porque pienso ir actualizándolo para usarlo seguido&#8230;
 
Caturra:/# cd usr/local/src/
Caturra:/usr/local/src# mkdir Gnome3
Caturra:/usr/local/src# cd Gnome3/
Caturra:/usr/local/src/Gnome3# bzr get lp:zeitgeist; bzr get lp:gnome-activity-journal
You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See &#8220;bzr help launchpad-login&#8221;.
Branched 1289 revision(s).
You have not informed bzr of your Launchpad ID, and you must do this to
write to Launchpad or access private data.  See &#8220;bzr help launchpad-login&#8221;.
Branched 258 revision(s).
Caturra:/usr/local/src/Gnome3# 
 
4.- Ejecutar:
 
Como $USER ejecutamos lo siguiente:
 
CdK1@Caturra:/usr/local/src/Gnome3/zeitgeist$ ./zeitgeist-daemon.py &
 CdK1@Caturra:/usr/local/src/Gnome3/gnome-activity-journal$ ./gnome-activity-journal 

 Con eso levantamos, para sacarle el máximo provecho hacemos:
 
Caturra:/# cd usr/local/src/Gnome3/zeitgeist/
Caturra:/usr/local/src/Gnome3/zeitgeist# ./autogen.sh
 Caturra:/usr/local/src/Gnome3/zeitgeist# make
 Caturra:/usr/local/src/Gnome3/zeitgeist# make install

 PD: He omitido la salida por ser innecesaria&#8230;
 
Con esto tenemos listo, lo que nos crea dos comandos:
 
zeitgeist-daemon   zeitgeist-datahub 
 
Y listoco&#8230;, ahora para ahorrarnos algunas cosas lo automatizamos:
 
Vamos a:
 
Sistema ==> Preferencias ==> Aplicaciones al inicio le damos a &#8220;Añadir&#8221; y agregamos:
 
Nombre: Gnome Zeitgeist
Comando: zeitgeist-daemon
Comentario: Nice
 
Con esto tenemos el demonio listo, agregamos GNOME Activity Journal
al Menú: para lo cual usamos &#8220;alacarte&#8221;.
 
5.- Actualizamos el código regularmente:
 
Creamos un archivo con el nombre que queramos, con algo similar a esto, es bastante rudimentario pero sirve&#8230;
 
#!/bin/bash

cd /usr/local/src/Gnome3/zeitgeist/ && bzr pull && sh autogen.sh && make && make install &&
 cd /usr/local/src/Gnome3/gnome-activity-journal/ && bzr pull
 
Le damos permiso de ejecución y lo alojamos en /etc/cron.daily o pueden user crontab -e etc&#8230;
 
Acá tienen un ejemplo de Zeitgeist y GNOME Activity Journal en su máxima expresión&#8230;
 
[http://seilo.geekyogre.com/2010/01/a-mockup-is-worth-a-thousand-lines-of-code/](http://seilo.geekyogre.com/2010/01/a-mockup-is-worth-a-thousand-lines-of-code/)

[http://segvfault.wordpress.com](http://segvfault.wordpress.com)

---

