---
title: "TFTP Server that allows concurrent connections"
date: 2008-07-22
forum: Server Platforms
---

### Post by rosscarroll on 2008-07-22
Hi all!!

I am in desperate, urgent need of a TFTP server that will work on Ubuntu with two requirements:

It must allow concurrent connections

It must allow us to set the server's source port as 69 (firewall or NAT support)



Bonus points for suggesting one that is easily configurable by a n00b like myself.


Many thanks for any suggestions!!

---

### Post by windependence on 2008-07-22
[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

[https://help.ubuntu.com/8.04/installation-guide/hppa/install-tftp.html](https://help.ubuntu.com/8.04/installation-guide/hppa/install-tftp.html)

Looks like it's just a matter of apt-get install the package and then configure as usual using the text file.

-Tim

---

### Post by rosscarroll on 2008-07-22
Many thanks. We have tried tftpd unsuccessfully - I can't see how to configure the port the server replies on. In our case it must be on port 69, and the normal tftp behaviour is to put the reply on any available port...

---

### Post by tybalt on 2008-10-03
You can try the -a or -R options in the setup of the server in inetd.conf. it would look like:
tftp		dgram	udp	wait	tftpd	/usr/sbin/tcpd	/usr/sbin/in.tftpd -R69:69 /srv/tftp
-a is for the ip:port to listen to
-R is to setup a range of ports to serve

Good luck!

---

