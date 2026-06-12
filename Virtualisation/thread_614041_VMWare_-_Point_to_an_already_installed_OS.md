---
title: "VMWare - Point to an already installed OS"
date: 2007-11-15
forum: Virtualisation
---

### Post by mesocal on 2007-11-15
Im running Gusty 7.10 for a few weeks and everything is great now.  I have it setup on my lenovo t61 laptop.  After a little configuring and reading a lot of posts,  i downloaded vmware server and used update-any-any-xxx and everything works great ( thank you ubuntu forums ).  

Is it possible to create a virutal machine with my XP which is already installed on my hard drive.  or do i need to use an OEM disk and to install XP.  im curious because lenovo, like most companies,  only send a few rescue disks with all the appropiate drivers and os info. 

This more of a learning project for me, then anything else.

---

### Post by anaconda on 2007-11-15
Yes it is possible, but xp will detect the hardware change (to vmwares virtual hardware) and might require re-activation.

---

### Post by mesocal on 2007-11-15
Thanks.  what do you mean by "xp will detect the hardware change"?  and how would i go about doing this. Could i lose any info if it fails?

---

### Post by mesocal on 2007-11-21
anyone have any more ideas about this?

---

### Post by ByteJuggler on 2007-11-21
VMWare has a Windows app that can convert running or remote windows machines to VM's.  It's called "VMWare Converter" See their site for more.  However, as you know, Windows XP uses activation, and will need re-activation if substantial hardware changes are made to the PC it's installed on. Since a migration to a VM is essentially changing every single thing in the machine (motherboard, video card, hard drive, network card etc.) it will almost certainly need re-activating.  Depending on whether you have an OEM or full retail license, this will either be not possible or possible, respectively.

---

### Post by spupy on 2007-11-21
Use the VMWare Converter or just install windows in the virtual machine. This will require just one activation. DON'T USE the installed Windows directly in VMWare. It will require activation each time you start it in VMWare after starting it normally (or vice versa), and this will burn your activation attempts pretty quickly. That is because for each major hardware change windows thinks it is installed freshly and would want activation code.  Thats the only concern when running existing windows partition. Otherwise there is no problem. 
If you fail to activate windows in 3 days (i.e. enter the registration code you have), that windows install becomes unusable.

---

