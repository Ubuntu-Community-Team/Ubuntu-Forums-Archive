---
title: "Building a boot server, need some assistance."
date: 2009-05-07
forum: Server Platforms
---

### Post by jms1989 on 2009-05-07
Hello, I an trying to setup a boot server on my home server but I run into road blocks on each article I try. My server runs ubuntu server 8.04 lts with a 500mhz processor, 248mb of ram, and a bucket load of disk space.

It currently runs as a webserver, a bittorrent downloader, file host for the download files, ssh server, and a few other small things. The main reason I want to setup a boot server is for experience and to build a collection of bootable utilities and os installers to help fix broken computers.

Now, I have installed tftpd-hpa and dhcp3 server but I couldn't get a spare machine to boot the bootloader. I'm not sure what's wrong. Please help.

PS. Known good resources are welcome and has anyone else successfully set one up, if so, can you please provide some tips?

---

### Post by jms1989 on 2009-05-09
Bump, anyone?

Btw, google has failed to find me some easy to understand guides that cover everything required to make it work.

---

### Post by koenn on 2009-05-09
this should get you in the right direction:

[http://users.telenet.be/mydotcom/howto/linux/diskless01.htm](http://users.telenet.be/mydotcom/howto/linux/diskless01.htm)

also, mind that for network boots to work, the network adaptor in the client machine needs to be bootable (eg PXE)

---

### Post by jms1989 on 2009-05-14
The dhcp info on that page helped and I found a link from a different thread on here that helped get tftp working.

This page helped: [http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

Now I just need to add my own entries. :)

---

