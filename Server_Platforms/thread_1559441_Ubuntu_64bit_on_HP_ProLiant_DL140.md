---
title: "Ubuntu 64bit on HP ProLiant DL140"
date: 2010-08-23
forum: Server Platforms
---

### Post by morbidchimp on 2010-08-23
Hi all,

I've been attempting a regular (base install) of Ubuntu 64bit on a HP ProLiant DL140 machine straight from the Ubuntu ISO I downloaded and burned and also from our PXE Server. 

Spec is; IDE 80gb HDD, RageXL GFX integrated, Xeon 64bit CPU, 2gb RAM, Broadcom Network Adapter

The problem I have is that during network hardware configuration it reports that it can't detect the network cards. 

I've searched both HP and Ubuntu sites and both say that Ubuntu 8-10 are certified by HP/Canonical to be supported. I am wondering, do I need to grab drivers for these devices somewhere else - the downloads on the HP site are RPM based for Red hat and such, nothing about Ubuntu - though I did find some leads to debian based sources which I have yet to look into. 

My question is this, if Ubuntu is considered certified for these devices should not the installer work with the network cards as is or does anyone know where I can get the drivers in DEB format?

Supported HP Servers
[http://webapps.ubuntu.com/certification/make/HP/servers/](http://webapps.ubuntu.com/certification/make/HP/servers/)

The page where it is reported as certified
[http://webapps.ubuntu.com/certification/hardware/200712-183/](http://webapps.ubuntu.com/certification/hardware/200712-183/)


The HP page relating to this server

[http://h10010.www1.hp.com/wwpc/pscmisc/vac/us/en/sm/proliant/dl140g3-qanda.html?jumpid=reg_R1002_USEN](http://h10010.www1.hp.com/wwpc/pscmisc/vac/us/en/sm/proliant/dl140g3-qanda.html?jumpid=reg_R1002_USEN)

I purchased 4 of these servers from Ebay (i taught did my research, at least premilimary) - and I have no problem getting down to the guts of it if I have to to make these work, just a starting point or a general direction from someone with some experience with these rack servers would be great. 

I'm assuming that although it says its supported and certified it means I still got to get the drivers from somewhere and perhaps compile from source as they are prob not likely supported from the CD as is?

Thanks in advance,

Ivan




Edit: it just dawned on me that maybe I need non-free drivers? as in proprietry?

Edit2: I've just discovered eBox 2 (zentyal) based on Ubuntu works out of the box with the network cards. I'll be looking further into it and will reply should I get any further

Edit3: During the install of eBox2 it said something about automaticly adding extra repositories, though I missed what it was for... maybe hardware, I'll check as soon as I can - install is still going


Edit4: It appears that on one of the four servers I have (all supposibly exactly the same machine) that neither ubuntu nor ebox are able to detect any network interfaces. Think that maybe it was this one machine that was causing me problems. I'll report back again later.



Turned out to be a non-issue - the two network cards in the machine I was having trouble with are damaged. The other 3 machines with the same network cards have no problems and Ubuntu supports it out of the box.

---

