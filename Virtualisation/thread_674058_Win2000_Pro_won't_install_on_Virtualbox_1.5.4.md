---
title: "Win2000 Pro won't install on Virtualbox 1.5.4"
date: 2008-01-21
forum: Virtualisation
---

### Post by mitsugiri on 2008-01-21
I'm having difficulty trying to install Windows 2000 Pro as a guest operating system on my Ubuntu 7.10 Host.  The install CD loads all the necessary files and gets stuck where it says "Setup is starting Windows 2000".  I don't even get to the part where it says "To install Windows 2000 hit ENTER"

I tried installing Windows XP and that installs fine.

Anybody else come across this?  Experienced Virtualbox users: any suggestions?

Thanks

The specifics of my system is on my signature.

---

### Post by mitsugiri on 2008-01-22
Help! Anybody?

---

### Post by Cammy on 2008-01-22
I have a Win2k/Ubuntu dual boot, but I installed Win2k first, standalone, then hooked up my second hard drive and made it the master, with Win2k the slave, and it automatically set up the dual boot.  I was always under the impression that it had to be done that way, I dunno.

Maybe try pulling the ubuntu drive and installing Win2k standalone, then putting the Ubuntu drive back in and manually editing your boot menu?

---

### Post by mitsugiri on 2008-01-22
I think you misunderstood me. I want to create a virtual Win2000 machine on Ubuntu using Virtualbox.

---

### Post by FrankVdb on 2008-01-23
I remember when installing VirtualBox and reading its manual (which, btw, is well-written) that there is a special remark concerning Windows 2000. I'll try to find it and let you know.

---

### Post by FrankVdb on 2008-01-23
I just found the special chapter concerning Windows 2000. There is a bug in the hard disk driver that comes with W2K causing problems when installing in a virtual machine. 

You can find the explanation and the workaround on page 112 of the VirtualBox 1.5.4 user manual (chapter 11.2.2).

Link to the manual: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by mitsugiri on 2008-01-23
> **FrankVdb said:**
> I just found the special chapter concerning Windows 2000. There is a bug in the hard disk driver that comes with W2K causing problems when installing in a virtual machine. 

You can find the explanation and the workaround on page 112 of the VirtualBox 1.5.4 user manual (chapter 11.2.2).

Link to the manual: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Thanks FrankVdb, I tried that already and it did not work for me.

---

