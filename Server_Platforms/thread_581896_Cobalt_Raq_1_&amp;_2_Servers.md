---
title: "Cobalt Raq 1 &amp; 2 Servers"
date: 2007-10-19
forum: Server Platforms
---

### Post by johng4 on 2007-10-19
I've recently come into about 8 raq1s and raq2s, since the NOC at my job is clearing out all their old web/mail servers to be replaced by Plesk servers.

I've seen a walk through on setting up debian sarge (3.1) on a RaQ1 and RaQ2, but have heard mixed results on getting it to work.  I'm wondering if anyone out there has been able to compile a MIPS-compatible kernel to work with Ubuntu on a Raq1/2.

I also came into a Raq3 which is a i386-based arch.  Anyone been able to netboot/install Ubuntu on one of these?  If so, how?

My planned method for the Raq3 is to try and get the netboot to work with a PXE server I'm currently building.

Ultimately, if I can't get Ubuntu to install on these RaQs, I'm going to set them up with a 2.4 debian install, and use some OpenMosix patches to put them into a Beowulf cluster.  I want to get at least one of the raq1/2s with Ubuntu though.

Hopefully when the NOC starts getting rid of our raq 550s, I'll be first in line this time around.  I missed out on all the raq4s this time around. :(

---

### Post by johng4 on 2007-10-20
Somewhere out there I know someone has a raq1/2 with Ubuntu on it...

---

### Post by filtertrap on 2007-10-24
Well I would surely use Debian and I mean Etch BTW...you will run into nothing but trouble using older kernels if you install Debian on the MIPS machine. It just works now whereas before it was like pulling dinosaur teeth. Setup an NFS and DHCP server...put the mac address into the dhcp config...slap in the nfs.root(untar it)...export it...set the Cobalt to netboot mode...which is a key combination  both left and right arrow keys(play around and find it) then let her rip.

Then you have an up to date machine without all the super old packages. You really don't want to use Ubuntu Server on the Cobalt...there is a lot to fix in there. I run it now and I had to do more than I thought to get it going the way I wanted it. OpenSSH server doesn't come with Ubuntu Server 7.x, but you have LAMP lol...WTF

Netboot is there...just have your tftp server or the above method and shoot out your image and you are cruising.

---

