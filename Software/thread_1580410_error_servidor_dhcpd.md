---
title: "error servidor dhcpd"
date: 2010-09-23
forum: Software
---

### Post by asterix77 on 2010-09-23
Al ejecutar lo siguiente en consola para iniciar el servidor dhcp me aparece el siguiente error.

$ sudo /etc/init.d/dhcp3-server start
dhcpd self-test failed. Please fix the config file.
The error was: 
Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
/etc/dhcp3/dhcpd.conf line 124: semicolon expected.
                option 
                                ^
Configuration file errors encountered -- exiting

He buscado el archivo de configuración y he mirado la linea 124 donde hay al final un punto y coma, el cual he intentado quitarlo, colocarlo, dejar un espacio e insertarlo, reemplazarlo por una coma, etc, etc. Pero no logro solucionar el problema

Aquí están las lineas del archivo en cuestión.

subnet 192.168.2.0 netmask 255.255.255.0 {
                option domain-name-servers;
               ** option subnet-mask 255.255.255.0;**
                option routers 192.168.2.3;
                range 192.168.2.4 192.168.2.254;
                }

Lo que está en negrita es la famosa linea 124.

Se agradece cualquier comentario al respecto. Por cierto mi sistema es lucid AMD64.

Saludos

---

