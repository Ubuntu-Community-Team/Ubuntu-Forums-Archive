---
title: "Clientes Ligeros Ubuntu"
date: 2012-04-26
forum: Uruguay Team
---

### Post by xGrp on 2012-04-26
Buenas gente

Tengo en la oficina donde trabajo un par de maquinas viejitas P3 y 2 P2, me gustaria montar una red de clientes ligeros como test,
cuento con una red y las pc pueden bootear desde la placa de red, si alguien ya lo hizo o tiene algun link para  consultar que me fascilite barbaro mientras seguire buscando por la red un poco mas de info

uso Ubuntu 11.10

Objetivo 

Montar un Servidor que provea un SO por red a las pc 

encontre mucha info sobre instalar por red pero me gustaría saber si puedo arrancarlas cargarles en memoria el SO y trabajar usando las aplicaciones del server 

Gracias

---

### Post by guillermolisi on 2012-04-27
Lo primero que se me ocurre es utilizar [LTSP]("https://help.ubuntu.com/community/UbuntuLTSP").

Luego, hay otras formas de implementar lo que queres hacer pero las maquinas con PII cuyo procesador no contenga la instruccion CMOV no funcionaran con versiones modernas del kernel Linux.

---

### Post by xGrp on 2012-04-27
bueno mira ya empece a hacer pruebas pero me lio con el dhcp3 intento arrancarlo pero no quiere 

te comento lo que he empezado con info recopilada por la web

Instalo la herramienta que tu dices

$ sudo apt-get install ltsp-server-standalone 

eso me instala un conjunto de cosas inclusive el dhcp3 y un tftp

reinicio el tftpd si esta parado arranca

$ sudo /etc/init.d/tftpd-hpa restart 

Creo la imagen que los clientes van a levantar

$ sudo ltsp-build-client 

I: Retrieving Release
I: Retrieving Release.gpg
I: Checking Release signature
I: Valid Release signature (key id 630239CC130E1A7FD81A27B140976EAF437D05B5)
I: Retrieving Packages
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
I: Checking component main on [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)...
I: Retrieving adduser
I: Validating adduser

...
...
...

Creating new configuration file
Adding new entry
The nbd-server daemon doesn't allow for live configuration update.
To pick up the changes, the daemon needs to be restarted.
If it's a new LTSP chroot. Run /etc/init.d/nbd-server restart
THIS WILL DISCONNECT ALL YOUR CLIENTS (they'll need to be rebooted)
información: la instalación del cliente LTSP se completó satisfactoriamente

reinicio el nb como ahi recomienda

$ sudo /etc/init.d/nbd-server restart

Restarting the Network Block Device server is pretty harsh on clients still using it.
waiting 5 seconds...You have been warned!
Restarting Network Block Device server: Stopping Network Block Device server: nbd-server.
 nbd-server.

EL PROBLEMA ES EL DHCP NO ENCUENTRO DONDE HACERLO ARRANCAR

 sudo /etc/init.d/isc-dhcp-server status
Status of ISC DHCP server: dhcpd is not running.

$ sudo /etc/init.d/isc-dhcp-server start
 * Starting ISC DHCP server dhcpd 
 * check syslog for diagnostics.  ------> fail

$ sudo /etc/init.d/isc-dhcp-server status
Status of ISC DHCP server: dhcpd is not running.

Que estare haciendo mal ? quizas no necesite el dhcp en esta version de Ubuntu?

Gracias Gillermo me pondre a buscar info sobre el CMOV de ultima instalo una VM con una Vesion de Ubntu mas vieja que haga de servidor de imagenes

---

### Post by guillermolisi on 2012-04-27
Normalmente, digo asi porque no use nunca LTSP asi que no se si mantiene el standard comunmente utilizado en Ubuntu, la configuracion del DHCP server se encuentra en /etc/dhcp3 y la del cliente en /etc/dhcp.

Cuando se presentan estos inconvenientes suele ser util mirar los logs del sistema: /var/log/dmesg; /var/log/messages; etc.

Para saber si un procesador incluye la instruccion CMOV, en una consola/terminal ingresas ```
sudo lshw
``` vas a obtener una larga lista detallada del hardware de tu PC. En particular la seccion que te debe interesar para este caso es la que menciona las caracteristicas de los nucleos del procesador. Ejemplo > *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.4.7
          serial: 0000-0F47-0000-0000-0000-0000
          slot: Socket 775
          size: 2996MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 214MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca [COLOR="Red"]cmov[/COLOR] pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm

---

### Post by xGrp on 2012-04-27
No joda esta de maravilla ese comando, es como un everest, genial yo desarrollo sistemas y la verdad que parezco un nene con jugete nuevo, ya me instale un par de herramietas de desarrollo para comenzar a tomar contacto 

Bueno siguiendo con el tema anterior voy a montar una VM con un adaptador de puente y vere que pasa a ver si se comunica con el host al menos te cuento que pasa pero lo hare en la noche que ahora ando corto de time

---

