---
title: "Instalar y Configurar LIRC para Receptor IR Serial"
date: 2010-02-23
forum: Software
---

### Post by lexer98 on 2010-02-23
Hola chicos preciso su ayuda necesito configurar el LIRC para un Receptor IR casero que hice que funciona por puerto serial ... en el windows funciona pero en ubuntu no logro instalarlo siguiendo este tutorial [http://www.mythtv.org/wiki/Ubuntu_Serial_Lirc_Install](http://www.mythtv.org/wiki/Ubuntu_Serial_Lirc_Install)
cuando pongo el segundo comando me tira este error

> lexer@Lexer-pc:/usr/src/linux$ sudo dpkg-reconfigure lirc-modules-source 
[sudo] password for lexer: 
Removing all DKMS Modules
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.

Error! Bad conf file.
File: /var/lib/dkms/lirc/0.8.6/source/dkms.conf does not represent
a valid dkms.conf file.Desde ya muchisimas gracias !

Pude arreglar lo primero puse el archivo dkms.conf en los sources y andubo pero ahora me tira otro error 

> lexer@Lexer-pc:~$ sudo dpkg-reconfigure lirc-modules-source 
Removing all DKMS Modules
Done.
Loading new lirc-0.8.6 DKMS files...
Building for architecture i686
Building initial module for 2.6.31-19-generic

Error! Bad return status for module build on kernel: 2.6.31-19-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/lirc/0.8.6/build/ for more information.

Por cierto mi version es Ubuntu 9.10

---

