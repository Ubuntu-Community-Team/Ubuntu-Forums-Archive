---
title: "Does anyone know how to do a tftp remapping so WinPE 3.0 will boot."
date: 2010-03-26
forum: Server Platforms
---

### Post by clivebuckwheat on 2010-03-26
I have checked several tutorial sites, to no avail. I can't seem to get Winpe 3.0 to boot over tftpd/pxe.

Has anyone successful done this using Ubuntu 9.10?, or am I just wasting my time trying.

---

### Post by HermanAB on 2010-03-26
Hmm, see the following link and scroll down to the TFTP paragraph:
[http://www.aeronetworks.ca/ris-howto.html](http://www.aeronetworks.ca/ris-howto.html)

---

### Post by clivebuckwheat on 2010-03-27
When I select the Winpe option in my menu, nothing happens

I checked \var\log\syslog

ar 27 02:01:27 pxe-server in.tftpd[9241]: tftp: client does not accept options
Mar 27 02:01:27 pxe-server dhcpd: DHCPREQUEST for 192.168.1.4 (192.168.1.195) from 08:00:27:f2:41:65 via eth1
Mar 27 02:01:27 pxe-server dhcpd: DHCPACK on 192.168.1.4 to 08:00:27:f2:41:65 via eth1.

How do I troubleshoot this?

---

### Post by HermanAB on 2010-03-27
Hmmm, try tcpdump, a fast google search connection, a big mug of coffee and a box of doughnuts...

Use an isolated network or cross-over cable for the debugging, so you don't get led astray by extraneous network traffic.

---

### Post by clivebuckwheat on 2010-03-27
[CENTER]I got the remapping working, but now I get this as WinPe 3.0 is loading. Here is my log

[IMG]http://j.imagehost.org/0083/Screenshot.png[/IMG]
[IMG]http://j.imagehost.org/view/0083/Screenshot[/IMG]




[LEFT]Mar 27 19:46:21 pxe-server in.tftpd[14743]: remap: input: \Boot\BCD
Mar 27 19:46:21 pxe-server in.tftpd[14743]: remap: rule 0: rewrite: /Boot\BCD
Mar 27 19:46:21 pxe-server in.tftpd[14743]: remap: rule 0: rewrite: /Boot/BCD
Mar 27 19:46:21 pxe-server in.tftpd[14743]: remap: done
Mar 27 19:46:21 pxe-server in.tftpd[14743]: RRQ from 192.168.1.5 filename \Boot\BCD remapped to /Boot/BCD
Mar 27 19:46:21 pxe-server in.tftpd[14744]: remap: input: \Boot\Fonts\wgl4_boot.ttf
Mar 27 19:46:21 pxe-server in.tftpd[14744]: remap: rule 0: rewrite: /Boot\Fonts\wgl4_boot.ttf
Mar 27 19:46:21 pxe-server in.tftpd[14744]: remap: rule 0: rewrite: /Boot/Fonts\wgl4_boot.ttf
Mar 27 19:46:21 pxe-server in.tftpd[14744]: remap: rule 0: rewrite: /Boot/Fonts/wgl4_boot.ttf
Mar 27 19:46:21 pxe-server in.tftpd[14744]: remap: done
Mar 27 19:46:21 pxe-server in.tftpd[14744]: RRQ from 192.168.1.5 filename \Boot\Fonts\wgl4_boot.ttf remapped to /Boot/Fonts/wgl4_boot.ttf
Mar 27 19:46:21 pxe-server in.tftpd[14744]: tftp: client does not accept options
Mar 27 19:46:21 pxe-server in.tftpd[14745]: remap: input: \Boot\Fonts\wgl4_boot.ttf
Mar 27 19:46:21 pxe-server in.tftpd[14745]: remap: rule 0: rewrite: /Boot\Fonts\wgl4_boot.ttf
Mar 27 19:46:21 pxe-server in.tftpd[14745]: remap: rule 0: rewrite: /Boot/Fonts\wgl4_boot.ttf
Mar 27 19:46:21 pxe-server in.tftpd[14745]: remap: rule 0: rewrite: /Boot/Fonts/wgl4_boot.ttf
Mar 27 19:46:21 pxe-server in.tftpd[14745]: remap: done
Mar 27 19:46:21 pxe-server in.tftpd[14745]: RRQ from 192.168.1.5 filename \Boot\Fonts\wgl4_boot.ttf remapped to /Boot/Fonts/wgl4_boot.ttf
Mar 27 19:46:22 pxe-server in.tftpd[14746]: remap: input: \hiberfil.sys
Mar 27 19:46:22 pxe-server in.tftpd[14746]: remap: rule 0: rewrite: /hiberfil.sys
Mar 27 19:46:22 pxe-server in.tftpd[14746]: remap: done
Mar 27 19:46:22 pxe-server in.tftpd[14746]: RRQ from 192.168.1.5 filename \hiberfil.sys remapped to /hiberfil.sys
Mar 27 19:46:22 pxe-server in.tftpd[14746]: sending NAK (1, File not found) to 192.168.1.5
[/LEFT]

[/CENTER]

---

