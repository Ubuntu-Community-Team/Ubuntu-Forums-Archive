---
title: "Server Edition + LTSP5 -- WTFM?"
date: 2007-05-06
forum: Server Platforms
---

### Post by Corvias on 2007-05-06
OK, one of the highlights of the newest release of Ubuntu Server was the inclusion of LTSP-5. Where the heck are the howtos? the wiki is sparse on the topic at best. Am I missing something?

---

### Post by bobsta63 on 2007-05-06
Yeah, I too have the same queston... Please could someone point us both in the right direction please:o

---

### Post by baastie on 2007-05-06
Hi,

mabye this will help...

[http://linuxagora.com/vbforum/showthread.php?p=3642](http://linuxagora.com/vbforum/showthread.php?p=3642)

It's pointed to Debian Etch.. but maybe some usefull info...

Cheers,

---

### Post by smhickel on 2007-05-07
Biggest issue we had was finding out that edubuntu has native support built in for LTSP. We converted from ubuntu to edubuntu. Part of that entails loading the ltsp files (not client though) from synaptic package manager.

Then set up the dhcp per the docs on the ubuntu website (google search edubuntu feisty ltsp)

That shows how to configure dhcp.conf under /etc/ltsp/dhcpd.conf.

Key for us was to not have a / in front of ltsp (see my other post under ltsp ubuntu general forum from a few days ago.

authoritative;  
  
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.150 192.168.1.155;
  option domain-name "your_domain_name_here.com";
  option domain-name-servers 192.168.1.50;
  option broadcast-address 192.168.1.255;
  option routers 192.168.1.117;
  option subnet-mask 255.255.255.0;

 
  filename "ltsp/i386/pxelinux.0";
  option root-path "/opt/ltsp/i386";
}

** If you are using windows dhcp, then do the equivalent of the above in there. Not sure how but have seen stuff here on that in other posts.

Then we did the following:

 313  cd /usr/sbin
  314  ls
  315  ./ltsp-build-client 

This downloads the client and configures it in the /opt/ltsp/i386 directory.

then 

  /etc/init.d/dhcp3-server start
 
Should just start working now.

---

### Post by jimcooncat on 2007-05-09
[http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)

"Ubuntu Server edition includes thin client support using LTSP (Linux Terminal Server Project). LTSP-5, the latest release, offers a simple installation and easy maintenance...."

I don't have a feeling of entitlement or anything -- I take that back, actually I do. If you advertise it, it should be in there, along with some instructions how to make it work. I wouldn't fret if this had just been some universe package.

I am so looking forward to playing with this when I redo my network this summer. Someone please find the manual!!!

------

With all that fuss, I just tried downloading and unpacking ltsp-server, and nosing around in there. Here's a jewel I found. Sounds pretty simple to me:

---- ltsp.5.0.7/server/doc/Quickinstall ----

This document aims to describe the quickest way to get a ltsp server 
running on an existing ubuntu or kubuntu (xubuntu comes with a ltsp 
option in the installer, edubuntu even sets up ltsp in its default 
install).

You need to set up one static interface where you will attach the 
thin clients, install two packages and run one command.

Configure your spare interface for the thin clients to have the 
IP 192.168.0.1, then run command below:

sudo apt-get install ltsp-server-standalone openssh-server

Now create your Thin Client environment on the server by running:

sudo ltsp-build-client

After that, you will be able to boot your first thin client. 
Note that if you want to use another IP than the above, you need to 
edit the /etc/ltsp/dhcpd.conf file to match the IP values and 
restart the dhcp server.

If you change the IP data after you have done the initial setup, 
please run the command sudo ltsp-update-sshkeys to make the ssh 
server aware of the change.

---

### Post by anco on 2007-05-28
Another negative experience with Ubuntu Server edition 7.04.

LTSP is really not at all right out of the box.... I ran two edubuntu servers 6.10 until now and tried to setup an Ubuntu server 7.04 ltsp this time.

Well bad advertising about this edition. It takes quite some work to setup the ltsp stuff no clear manual for 7.04 on the wiki. We have to search around in old wiki's to get it going, and still local devices don't startup no local cd, no local usb key or what so ever.... yes it is by default as local dev = true in the ltsp.conf.... But it still does not work for me :( 

Simply install edubuntu and it all works directly???? same server, same client station....  :o What am I missing with Ubuntu SERVER Ltsp right out of the box???? Bad move this time

I'll go back to Edubuntu. That just works... :p

---

### Post by anco on 2007-05-28
Well maybe I'll stay a little longer on Ubuntu SERVER 7.04.

If you search long enough Google will help you to find the right posts...
Basic LTSP setup seems to work now nearly as I'm used to in Edubuntu. 
Another post which help me to give me that little stupid detail to activate access to local devices
is the following link.

[https://wiki.edubuntu.org/EnableLTSP5LocalDevices](https://wiki.edubuntu.org/EnableLTSP5LocalDevices)

Now somehow the ltsp-manager is installed via synaptic, but nowhere in the menu's ? :o 

Thank you all for great wiki's and posts.

---

