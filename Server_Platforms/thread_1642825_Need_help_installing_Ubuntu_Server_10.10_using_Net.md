---
title: "Need help installing Ubuntu Server 10.10 using Network Boot+TFTPD32"
date: 2010-12-10
forum: Server Platforms
---

### Post by teekay13 on 2010-12-10
Hi, I'm new to network booting and I've come across TFTPD32 as an application to help install Ubuntu Server 10.10 on my 32-bit Gateway Solo 5300 so that I could use it as a test server. 

I am attempting this method since neither the cd drive or usb drive work properly (the usb only working after logging in). However, I currently have no OS after half installing Ubuntu and accidentally shutting it down after it deleted the hard drive's contents-BIG mistake. It currently only boots to a black screen and a flashing underscore in the top left corner.

I am wondering how to network boot because I have never done it before and I don't fully know what is involved. Below is some-things you might want to know about what I have in hand:

  -Old Gateway Solo 5300  Laptop with no OS(32 bit, 256MB RAM,       RJ-45 jack, 10 GB HDD)
  -Acer Aspire 570Z with Windows Vista Premium 32-bit(3GB RAM, 120GB HDD + RJ-45 jack)
       -STORED ON ACER ASPIRE=Ubuntu boot files, TFTPD32,            Unetbootin.
   -Blue Ethernet cable, Yellow crossover ethernet cable.
   -Router and modem

In total, what are the steps to have Ubuntu Server 10.10 edition succesfully installed on the old Gateway. Your help is appreciated,
TOM

---

### Post by ncwilde43 on 2010-12-11
First of all, I've only been using Ubuntu since March so I consider myself as a noob.

Recently I inherited a Dell P4 tower and decided to install Maverick Server on it and act as a PXE server for my monthly reformats.

Here are the steps in which I used to setup my network boot.

- had router act as my DHCP server
- installed 10.10 server on my P4 tower
- assigned a static IP to my server
- installed tftpd-hpa
  - downloaded the entire [maverick netboot directory]("http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/netboot/") to my tftpboot directory. (the version I want to be installed).
- installed [dnsmasq]("https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP") (addresses issues with having router acting as DHCP server).
  - created a ltsp.conf file in my /etc/dnsmasq.d/ directory that points to the pxelinux.0 file located in the tftpboot directory.

Here is my current 'understanding' of what happens during the PXE installation:

 - Client computer boots with PXE boot enabled.
 - router/server assigns an IP to the client.
 - client requests a PXE boot image.
 - dnsmasq tells the client to boot the pxelinux.0 image.
 - pxelinux.0 loads the 'default' file located in tftpboot/pxelinux.cfg directory.
 - the default file loads the menu.cfg file located in the tftpboox/ubuntu-installer/i386/boot-screens/ directory.
 - the menu.cfg file launches the initrd.gz and linux files which then launches the netboot install program.

A few side notes if you're going to be performing multiple installs:
 - use a [preseed]("https://help.ubuntu.com/10.10/installation-guide/i386/appendix-preseed.html") file to automate the installations.
 - use [apt-cacher]("https://help.ubuntu.com/community/Apt-Cacher-Server") to save install time by caching the downloaded install files.

Lastly, [here's]("http://ubuntuforums.org/showthread.php?t=1491537") a link to a previous PXE related post.

Let me know if you need any other help.

---

