---
title: "Making the switch"
date: 2007-08-08
forum: The Cafe
---

### Post by nickburns on 2007-08-08
I got my hands on a nice 64 bit machine, but I am unsure if I should switch. My concerns are can I run 32 bit application? all 32 or just selected? will I really see a difference? a big difference or small?

Can I still run these mission critical applications:

VMWare
gDesklets
phpmyadmin
apache
samba, smbfs,
open office
and evolution?

Please everyone give me some feedback...

---

### Post by yatt on 2007-08-09
Flash is going to take a few extra steps to install. You need to use nspluginwrapper (in the Ubuntu repo, IIRC. It is in the Debian one for sure) to make it appear to be a 64bit plugin for FF. There are howtos on this forum, but Debian has a package that will do this for you.

There also is not a Java plugin. There is Java, but for some reason the 64bit Java does not include a plugin. The 32bit Java plugin does not work with nspluginwrapper either.

Those are the main things you will notice. If an app is open source, it should run fine on 64bit.

---

### Post by Spr0k3t on 2007-08-09
VMWare - I don't use (should work)
gDesklets - I don't use (should work)
phpmyadmin - Works
apache - Like a champ
samba, smbfs, - Works
open office - Very slick in 64bit
and evolution? - Works good

The only area you may have problems with is if you want to use WINE (I don't use it here), and the 32bit Flash plugin.  Outside of that... I've not had any problems.  I have both 32bit and 64bit on my main system... the 64bit is noticeably faster.

---

### Post by Dr. C on 2007-08-09
I have used VMWare Server on 64bit Ubuntu Edgy and Feisty  and it works great. 

One advantage over the 32 bit version is that you can run 64bit guest operating systems, GNU / Linux, Solaris and Microsoft Windows, as well as the 32 bit versions of GNU / Linux, Solaris and Microsoft Windows and 8 /16 bit (MS DOS / Windows 3.xx) guests.

---

### Post by nickburns on 2007-08-09
I put in a 64 bit cd and boot up on the live cd and if I run 'top' in the terminal I only show the 3.2 g of ram, but my system has 4 gigs.  Does this mean that 64bit will not work on my motherboard?  I thought that when I go 64 I can get over the 3.2 gig limit.

Does the live cd only allow 3.2 or does this mean I am limited with hardware or what?

I have a Dell Dimension 5150, with the dual core 64bit processors (4 gigs of ram.)

---

