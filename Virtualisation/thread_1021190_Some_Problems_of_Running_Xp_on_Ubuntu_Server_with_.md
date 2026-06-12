---
title: "Some Problems of Running Xp on Ubuntu Server with Virtualbox"
date: 2008-12-25
forum: Virtualisation
---

### Post by dtone on 2008-12-25
Hello,everyone.

Merry Christmas~

I've got some troubles when I try to install windows xp as a guest system on ubuntu server 8.04 LTS (host) with VirtualBox-ose. I hope someone will give me some tips to solve the problems. 

I run the command lines as following to build a xp platform:
> vboxmanage createvm -name xplite -register
> vboxmanage createvdi -filename xplite.vdi -size 10000 -register
> vboxmanage modifyvm xplite -hda xplite.vdi
> vboxmanage modifyvm xplite -memory 512MB -acpi on -boot1 dvd -nic1 nat
> vboxmanage registerimage dvd /tmp/xplite.iso
> vboxmanage modifyvm xplite -dvd /tmp/xplite.iso
> vboxmanage startvm xplite

---------------------------------------------------------------
The only line display on the screen is :

Waiting for the remote session to open...

and nothing more appear since I waited for a long time.
I have tried several times, attributing to the same result.
Will you give me any advise?

---

### Post by namdung on 2008-12-25
Do u have a GUI installed?

I suggest u uninstall the Virtualbox OSE, download the Hardy from the following link and reinstall. 
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by dtone on 2008-12-25
Ok&#65292;I'll have a try. Thanks very much

---

