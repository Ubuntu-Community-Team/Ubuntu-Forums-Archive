---
title: "Compartir Impresoras y carpetas entre Ubuntus"
date: 2009-01-03
forum: Software
---

### Post by NickCis on 2009-01-03
Hola, yo tengo dos maquinas Ubuntu, ambas en su vercion 8.04. Una tiene de Wm, Openbox, y es una instalacion minima, la otra tiene el ubuntu con instalacion desktop, y funciona como server para compartir la internet.

Lo que nececito ahora es compartir carpetas entre estas dos pc's.
Ademas, la que actua como "server" para compartir internet tiene conectada una impresora, que tambien quiero que la otra pc la pueda usar.

Por lo que lei, era algo de Samba, pero Samba es el protocolo para Red de WIn, ( [http://ubuntu-ar.org/tutoriales/samba](http://ubuntu-ar.org/tutoriales/samba) ), en este caso yo tengo dos Ubuntu. Tengo que utilizar samba igual?, o hay algo especifico para linux?.

Como puedo lograr esto?.

Saludos.

---

### Post by sergiom99 on 2009-01-03
el tutorial ese está perfecto. Lo hizo faktorqm (Martín).
Siguiendolo, yo configuré para compartir carpetas entre un Xubuntu y un Kubuntu.
Nunca lo probé con impresoras.
Suerte!

---

### Post by Hei Ku on 2009-01-04
Hmmm, el tutorial que tenés que usar es el de NFS, que es el protocolo nativo de Linux.

[http://ubuntu-ar.org/node/208](http://ubuntu-ar.org/node/208)

Para compartir impresoras se usa CUPS, acá hay un tutorial de la wiki de ubuntu-es

[http://doc.ubuntu-es.org/Impresi%C3%B3n_en_red_con_Ubuntu](http://doc.ubuntu-es.org/Impresi%C3%B3n_en_red_con_Ubuntu)

---

### Post by NickCis on 2009-01-04
Ok, muchas gracias, ahora pruebo los tutoriales.

Una pregunta, en la pc que esta actuando como server, cuando arracanca, casi al finalizar de cargar la pantalla de ubuntu (la que tiene la barra cuando esta cargando SO), salta a una pantalla de comando y se qeda mucho tiempo cargando el CUPS, y dsp no tira el cartelito de Ok, como hace con lo demas.
Eso es normal?.COmo puedo arreglarlo?

Saludos.

---

### Post by Hei Ku on 2009-01-04
No, no es normal. Podrias fijarte en los logs. daemon.log y boot.log pueden tener algo.

---

### Post by NickCis on 2009-01-04
En este ultimo boot, no me paso lo de qedarse esperando, entro normal, parece que la maquina hace lo que qiere xD, cuando se me qede lo posteo.

Ahora, tengo un problema para compartir las carpetas, instale los nfs-common nfs-kernel-server y configure el archivo "/etc/exportfs", que en mi pc no existia, lo tuve que crear. Pero, al ejecutar "sudo exportfs", no me devuelve nada (me tendria que devolver las carpetas que puse para compartir), como se puede soluciono esto? (Intente montar las carpetas en la maqina cliente y tampoco pude)

Saludos.

-----------
Edit: Buscando un poco mas por google me di cuenta, que el archivo que habia que modificar era "/etc/exports" y no "/etc/exportfs", y despues de modificarlo habia que ejecutar "exportfs -a" para que cargala las modificaciones.

Fuente: [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

-----------------
Ahora tengo problemas para compartir un disco Ntfs, que tengo en el Ubuntu que actua como servidor, cuando ejecuto "exportfs -a", me devuelve "exportfs: Warning: /media/disk does not support NFS export.

---

### Post by Hei Ku on 2009-01-04
Podes postear tu archivo exports?

EDIT: Por lo que vi, puede tener que ver con el tipo de filesystem que es /media/disk. Si se monta por FUSE, hay un bug en Ubuntu que no permite montarlo. Qué contiene esa carpeta?

EDIT2: Puede estar relacionado a este bug: [https://bugs.launchpad.net/ubuntu/+bug/159004](https://bugs.launchpad.net/ubuntu/+bug/159004)

---

### Post by NickCis on 2009-01-06
Archivo "/etc/exports"
```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/media/disk	10.8.16.2(rw,no_subtree_check,sync)
/home/newpc	10.8.16.2(rw,no_subtree_check,sync)
```

"/media/disk" es un disco NTFS, d windows, que tiene musica y otras cosas, que se monta automaticamente en el inicio de ubuntu.
Posteo mi "/etc/fstab"
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1e7aa1d8-2531-472a-8dea-1b9e8921c626 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=ceaad71d-2ed4-4285-bc74-8118ed51b525 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1 /media/disk ntfs defaults,rw,user,auto,iocharset=utf8,umask=000 0 0
```

Si, es algo parecido. Ahi el problema es con otra vercion de Ubuntu, y intentando compartir un disco fat32, mi problema es con una unidad montada en NTFS, pero basicamente es el mismo error.

Es un bug?, tendria que postearlo ahi?. Nunk reporte un bug, asi que si tengo que hacerlo, que alguien me expliqe como lo hago :P

Edit: agrego info del problema que se me queda cargando en el inicio de Ubuntu. Ayer, 5/1/09 a las 19:50 aprox, me paso, copio el /var/log/daemon.log (la parte relacionada con esa fecha):

```
Jan  5 19:48:11 ubuntu-newpc NetworkManager: <info>  starting... 
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: Successfully dropped root privileges.
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: avahi-daemon 0.6.22 starting up.
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: Successfully called chroot().
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: Successfully dropped remaining capabilities.
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: No service file found in /etc/avahi/services.
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.100.10.
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: New relevant interface eth1.IPv4 for mDNS.
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.8.16.1.
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: New relevant interface eth0.IPv4 for mDNS.
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: Network interface enumeration completed.
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: Registering new address record for fe80::2e0:4cff:fe0b:9e40 on eth1.*.
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: Registering new address record for 192.168.100.10 on eth1.IPv4.
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: Registering new address record for 10.8.16.1 on eth0.IPv4.
Jan  5 19:48:11 ubuntu-newpc avahi-daemon[5197]: Registering HINFO record with values 'I686'/'LINUX'.
Jan  5 19:48:12 ubuntu-newpc avahi-daemon[5197]: Server startup complete. Host name is ubuntu-newpc.local. Local service cookie is 3495949528.
Jan  5 19:48:20 ubuntu-newpc dhclient: DHCPREQUEST of <null address> on eth1 to 192.168.100.1 port 67
Jan  5 19:48:20 ubuntu-newpc dhclient: DHCPACK of 192.168.100.10 from 192.168.100.1
Jan  5 19:48:21 ubuntu-newpc dhclient: bound to 192.168.100.10 -- renewal in 15 seconds.
Jan  5 19:48:36 ubuntu-newpc dhclient: DHCPREQUEST of <null address> on eth1 to 192.168.100.1 port 67
Jan  5 19:48:36 ubuntu-newpc dhclient: DHCPACK of 192.168.100.10 from 192.168.100.1
Jan  5 19:48:37 ubuntu-newpc dhclient: bound to 192.168.100.10 -- renewal in 14 seconds.
Jan  5 19:48:51 ubuntu-newpc dhclient: DHCPREQUEST of <null address> on eth1 to 192.168.100.1 port 67
Jan  5 19:48:51 ubuntu-newpc dhclient: DHCPACK of 192.168.100.10 from 192.168.100.1
Jan  5 19:48:52 ubuntu-newpc dhclient: bound to 192.168.100.10 -- renewal in 13 seconds.
Jan  5 19:49:04 ubuntu-newpc ntpdate[4372]: can't find host ntp.ubuntu.com 
Jan  5 19:49:04 ubuntu-newpc ntpdate[4372]: no servers can be used, exiting
Jan  5 19:49:04 ubuntu-newpc ntpd[5281]: ntpd 4.2.4p4@1.1520-o Fri Mar  7 20:24:07 UTC 2008 (1)
Jan  5 19:49:04 ubuntu-newpc ntpd[5282]: precision = 1.000 usec
Jan  5 19:49:04 ubuntu-newpc ntpd[5282]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jan  5 19:49:04 ubuntu-newpc ntpd[5282]: Listening on interface #1 wildcard, ::#123 Disabled
Jan  5 19:49:04 ubuntu-newpc ntpd[5282]: Listening on interface #2 lo, ::1#123 Enabled
Jan  5 19:49:04 ubuntu-newpc ntpd[5282]: Listening on interface #3 eth1, fe80::2e0:4cff:fe0b:9e40#123 Enabled
Jan  5 19:49:04 ubuntu-newpc ntpd[5282]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jan  5 19:49:04 ubuntu-newpc ntpd[5282]: Listening on interface #5 eth0, 10.8.16.1#123 Enabled
Jan  5 19:49:04 ubuntu-newpc ntpd[5282]: Listening on interface #6 eth1, 192.168.100.10#123 Enabled
Jan  5 19:49:04 ubuntu-newpc ntpd[5282]: kernel time sync status 0040
Jan  5 19:49:04 ubuntu-newpc ntpd[5282]: frequency initialized -67.089 PPM from /var/lib/ntp/ntp.drift
Jan  5 19:49:05 ubuntu-newpc dhclient: DHCPREQUEST of <null address> on eth1 to 192.168.100.1 port 67
Jan  5 19:49:05 ubuntu-newpc dhclient: DHCPACK of 192.168.100.10 from 192.168.100.1
Jan  5 19:49:06 ubuntu-newpc dhclient: bound to 192.168.100.10 -- renewal in 12 seconds.
Jan  5 19:49:09 ubuntu-newpc NetworkManager: <debug> [1231192149.443663] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDRAM_GSA_H42N'). 
Jan  5 19:49:09 ubuntu-newpc hcid[5626]: Bluetooth HCI daemon
Jan  5 19:49:09 ubuntu-newpc hcid[5626]: Starting SDP server
Jan  5 19:49:09 ubuntu-newpc hcid[5626]: Created local server at unix:abstract=/var/run/dbus-SDYAAmgZiP,guid=59433feb259982339644e1ad49628055
Jan  5 19:49:09 ubuntu-newpc audio[5639]: Bluetooth Audio daemon
Jan  5 19:49:09 ubuntu-newpc NetworkManager: <debug> [1231192149.566726] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jan  5 19:49:09 ubuntu-newpc audio[5639]: Unix socket created: 5
Jan  5 19:49:09 ubuntu-newpc audio[5639]: audio.conf: Key file does not have key 'Enable'
Jan  5 19:49:09 ubuntu-newpc audio[5639]: audio.conf: Key file does not have key 'Disable'
Jan  5 19:49:09 ubuntu-newpc input[5643]: Bluetooth Input daemon
Jan  5 19:49:09 ubuntu-newpc input[5643]: Registered input manager path:/org/bluez/input
Jan  5 19:49:09 ubuntu-newpc audio[5639]: add_service_record: got record id 0x10000
Jan  5 19:49:09 ubuntu-newpc audio[5639]: audio.conf: Key file does not have key 'Disable'
Jan  5 19:49:09 ubuntu-newpc audio[5639]: audio.conf: Key file does not have group 'A2DP'
Jan  5 19:49:09 ubuntu-newpc last message repeated 3 times
Jan  5 19:49:09 ubuntu-newpc audio[5639]: SEP 0x806d0e0 registered: type:0 codec:0 seid:1
Jan  5 19:49:09 ubuntu-newpc audio[5639]: add_service_record: got record id 0x10001
Jan  5 19:49:09 ubuntu-newpc audio[5639]: add_service_record: got record id 0x10002
Jan  5 19:49:09 ubuntu-newpc audio[5639]: add_service_record: got record id 0x10003
Jan  5 19:49:09 ubuntu-newpc audio[5639]: Registered manager path:/org/bluez/audio
Jan  5 19:49:18 ubuntu-newpc dhclient: DHCPREQUEST of <null address> on eth1 to 192.168.100.1 port 67
Jan  5 19:49:18 ubuntu-newpc dhclient: DHCPACK of 192.168.100.10 from 192.168.100.1
Jan  5 19:49:19 ubuntu-newpc dhclient: bound to 192.168.100.10 -- renewal in 13 seconds.
Jan  5 19:49:32 ubuntu-newpc dhclient: DHCPREQUEST of <null address> on eth1 to 192.168.100.1 port 67
Jan  5 19:49:32 ubuntu-newpc dhclient: DHCPACK of 192.168.100.10 from 192.168.100.1
Jan  5 19:49:33 ubuntu-newpc dhclient: bound to 192.168.100.10 -- renewal in 13 seconds.
Jan  5 19:49:46 ubuntu-newpc dhclient: DHCPREQUEST of <null address> on eth1 to 192.168.100.1 port 67
Jan  5 19:49:46 ubuntu-newpc dhclient: DHCPACK of 192.168.100.10 from 192.168.100.1
Jan  5 19:49:47 ubuntu-newpc dhclient: bound to 192.168.100.10 -- renewal in 13 seconds.
Jan  5 19:50:00 ubuntu-newpc dhclient: DHCPREQUEST of <null address> on eth1 to 192.168.100.1 port 67
Jan  5 19:50:04 ubuntu-newpc dhclient: DHCPREQUEST of <null address> on eth1 to 192.168.100.1 port 67
Jan  5 19:50:14 ubuntu-newpc dhclient: DHCPREQUEST of <null address> on eth1 to 255.255.255.255 port 67
Jan  5 19:50:17 ubuntu-newpc avahi-daemon[5197]: Withdrawing address record for 192.168.100.10 on eth1.
Jan  5 19:50:17 ubuntu-newpc avahi-daemon[5197]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.100.10.
Jan  5 19:50:17 ubuntu-newpc avahi-daemon[5197]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan  5 19:50:17 ubuntu-newpc avahi-autoipd(eth1)[6077]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Jan  5 19:50:17 ubuntu-newpc avahi-autoipd(eth1)[6077]: Successfully called chroot().
Jan  5 19:50:17 ubuntu-newpc avahi-autoipd(eth1)[6077]: Successfully dropped root privileges.
Jan  5 19:50:17 ubuntu-newpc avahi-autoipd(eth1)[6077]: Starting with address 169.254.5.82
Jan  5 19:50:21 ubuntu-newpc ntpd_initres[6067]: host name not found: ntp.ubuntu.com
Jan  5 19:50:21 ubuntu-newpc ntpd_initres[6067]: couldn't resolve `ntp.ubuntu.com', giving up on it
Jan  5 19:50:22 ubuntu-newpc avahi-autoipd(eth1)[6077]: Callout BIND, address 169.254.5.82 on interface eth1
Jan  5 19:50:22 ubuntu-newpc avahi-daemon[5197]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.5.82.
Jan  5 19:50:22 ubuntu-newpc avahi-daemon[5197]: New relevant interface eth1.IPv4 for mDNS.
Jan  5 19:50:22 ubuntu-newpc avahi-daemon[5197]: Registering new address record for 169.254.5.82 on eth1.IPv4.
Jan  5 19:50:23 ubuntu-newpc avahi-daemon[5197]: Invalid legacy unicast query packet.
Jan  5 19:50:23 ubuntu-newpc avahi-daemon[5197]: Received response with invalid source port 1024 on interface 'eth1.0'
Jan  5 19:50:23 ubuntu-newpc avahi-daemon[5197]: Invalid legacy unicast query packet.
Jan  5 19:50:23 ubuntu-newpc NetworkManager: <info>  Updating allowed wireless network lists. 
Jan  5 19:50:23 ubuntu-newpc NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jan  5 19:50:23 ubuntu-newpc avahi-daemon[5197]: Invalid legacy unicast query packet.
Jan  5 19:50:23 ubuntu-newpc avahi-daemon[5197]: Received response with invalid source port 1024 on interface 'eth1.0'
Jan  5 19:50:26 ubuntu-newpc last message repeated 3 times
Jan  5 19:50:26 ubuntu-newpc avahi-autoipd(eth1)[6077]: Successfully claimed IP address 169.254.5.82
Jan  5 19:50:26 ubuntu-newpc avahi-autoipd(eth1)[6077]: Got SIGTERM, quitting.
Jan  5 19:50:26 ubuntu-newpc avahi-autoipd(eth1)[6077]: Callout STOP, address 169.254.5.82 on interface eth1
Jan  5 19:50:26 ubuntu-newpc avahi-daemon[5197]: Withdrawing address record for 169.254.5.82 on eth1.
Jan  5 19:50:26 ubuntu-newpc avahi-daemon[5197]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.5.82.
Jan  5 19:50:26 ubuntu-newpc avahi-daemon[5197]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan  5 19:50:26 ubuntu-newpc avahi-autoipd(eth1)[6078]: client: RTNETLINK answers: No such process
Jan  5 19:50:28 ubuntu-newpc dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Jan  5 19:50:28 ubuntu-newpc dhclient: DHCPOFFER of 190.189.156.6 from 190.189.144.1
Jan  5 19:50:28 ubuntu-newpc dhclient: DHCPREQUEST of 190.189.156.6 on eth1 to 255.255.255.255 port 67
Jan  5 19:50:28 ubuntu-newpc dhclient: DHCPACK of 190.189.156.6 from 190.189.144.1
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: Joining mDNS multicast group on interface eth1.IPv4 with address 190.189.156.6.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: New relevant interface eth1.IPv4 for mDNS.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: Registering new address record for 190.189.156.6 on eth1.IPv4.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: Withdrawing address record for 190.189.156.6 on eth1.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: Leaving mDNS multicast group on interface eth1.IPv4 with address 190.189.156.6.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: Joining mDNS multicast group on interface eth1.IPv4 with address 190.189.156.6.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: New relevant interface eth1.IPv4 for mDNS.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: Registering new address record for 190.189.156.6 on eth1.IPv4.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: Withdrawing address record for 190.189.156.6 on eth1.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: Leaving mDNS multicast group on interface eth1.IPv4 with address 190.189.156.6.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: Interface eth1.IPv4 no longer relevant for mDNS.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: Joining mDNS multicast group on interface eth1.IPv4 with address 190.189.156.6.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: New relevant interface eth1.IPv4 for mDNS.
Jan  5 19:50:28 ubuntu-newpc avahi-daemon[5197]: Registering new address record for 190.189.156.6 on eth1.IPv4.
Jan  5 19:50:28 ubuntu-newpc dhclient: bound to 190.189.156.6 -- renewal in 14088 seconds.
Jan  5 19:54:08 ubuntu-newpc console-kit-daemon[5501]: WARNING: Unable to activate console: No such device or address 
Jan  5 19:54:08 ubuntu-newpc init: tty4 main process (4743) killed by TERM signal
Jan  5 19:54:08 ubuntu-newpc init: tty5 main process (4744) killed by TERM signal
Jan  5 19:54:08 ubuntu-newpc init: tty2 main process (4748) killed by TERM signal
Jan  5 19:54:08 ubuntu-newpc init: tty3 main process (4749) killed by TERM signal
Jan  5 19:54:08 ubuntu-newpc init: tty6 main process (4751) killed by TERM signal
Jan  5 19:54:08 ubuntu-newpc init: tty1 main process (5854) killed by TERM signal
Jan  5 19:54:08 ubuntu-newpc avahi-daemon[5197]: Got SIGTERM, quitting.
Jan  5 19:54:08 ubuntu-newpc avahi-daemon[5197]: Leaving mDNS multicast group on interface eth1.IPv4 with address 190.189.156.6.
Jan  5 19:54:08 ubuntu-newpc avahi-daemon[5197]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.8.16.1.
Jan  5 19:54:08 ubuntu-newpc rpc.statd[4590]: Caught signal 15, un-registering and exiting.
Jan  5 19:54:11 ubuntu-newpc mountd[5382]: Caught signal 15, un-registering and exiting.
```

El boot.log, no lo encontre (lo busque con la herramienta de buscar y no me encontro nada). Donde esta?.

Saludos.

---

### Post by Hei Ku on 2009-01-06
Por lo que parece, es un bug hasta la version 8.04 con el driver ntfs.

Probá de montarlo como ntfs-3g, en vez de ntfs. En tu fstab, reemplaza ntfs por ntfs-3g. O hacelo desde el administrador de discos, como te sea más comodo.

---

### Post by Hei Ku on 2009-01-06
Por lo que parece, es un bug hasta la version 8.04 con el driver ntfs.

Probá de montarlo como ntfs-3g, en vez de ntfs. En tu fstab, reemplaza ntfs por ntfs-3g. O hacelo desde el administrador de discos, como te sea más comodo.

---

### Post by fmsismo on 2009-01-07
Para compartir impresoras también tenes el tuto en ubuntu-ar 
[http://ubuntu-ar.org/node/202](http://ubuntu-ar.org/node/202)

Saludos

---

### Post by NickCis on 2009-01-09
Lo monte como ntfs-3g y sigue con problemas para compartirlo. Si ejecuto "mount", me da  esta info de como monta el disco:
"/dev/sda1 on /media/disk type fuseblk (rw,noexec,nosuid,nodev,noatime,allow_other,blksize=4096)"
Se puede solucionar esto?

Saludos.

---

### Post by z37a on 2009-01-10
Gracias heiku, lo del nfs me vino de 10!!!!

---

### Post by Hei Ku on 2009-01-11
> **NickCis said:**
> Lo monte como ntfs-3g y sigue con problemas para compartirlo. Si ejecuto "mount", me da  esta info de como monta el disco:
"/dev/sda1 on /media/disk type fuseblk (rw,noexec,nosuid,nodev,noatime,allow_other,blksize=4096)"
Se puede solucionar esto?

Saludos.

Por lo que parece, es un error de ubuntu entre fuse y nfs. Si con el ntfs-3g no anda, lo más fácil va a ser que uses samba para compartir ese disco.

---

