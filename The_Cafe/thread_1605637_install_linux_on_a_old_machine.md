---
title: "install linux on a old machine"
date: 2010-10-25
forum: The Cafe
---

### Post by ged25 on 2010-10-25
I have an old laptop on which I'd like to install a lightweight distro. My problem is that it doesn't have a cd drive and it cannot boot of a flash drive. How can I install it?

---

### Post by koenn on 2010-10-25
does it have a floppy disk drive ?

---

### Post by KiwiNZ on 2010-10-25
I think the only Boot it is worth is a boot clear across your back yard into your waste bin :p;)

---

### Post by FuturePilot on 2010-10-25
Pxe

---

### Post by kaldor on 2010-10-25
I was in that situation too. 8 MB of ram and a bricked Windows 95 that refused to boot. No use.

---

### Post by Moozillaaa on 2010-10-25
> **KiwiNZ said:**
> I think the only Boot it is worth is a boot clear across your back yard into your waste bin :p;)


**Not very [COLOR=Green]Enviro-friendly[/COLOR] ...** [-X

---

### Post by koenn on 2010-10-25
> **KiwiNZ said:**
> I think the only Boot it is worth is a boot clear across your back yard into your waste bin :p;)

you need to talk to K.Mandla

[http://kmandla.wordpress.com/2009/04/11/three-reasons-to-buy-an-old-computer/](http://kmandla.wordpress.com/2009/04/11/three-reasons-to-buy-an-old-computer/)

[http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/](http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/)

---

### Post by mrtomservo on 2010-10-25
You might want to try pulling the hard drive from the old pc.  Using a laptop-IDE/USB adapter, put it in another pc just to install the OS, and plug it back into the old PC.  I've done that a few times when the old systems wouldn't support PXE, also had to do it on a netbook recently that wouldn't boot via USB.  Good for you for trying to find a use for an older machine!

---

### Post by KiwiNZ on 2010-10-25
> **Moozillaaa said:**
> **Not very [COLOR=Green]Enviro-friendly[/COLOR] ...** [-X

I was referring to one of these ......

---

### Post by undecim on 2010-10-25
Debian's (and Ubuntu's) net install isos use only the kernel and the initrd, which means the drive they're loaded from aren't mounted. So if you have an external hard drive case that fits the drive, you can put a net install iso on it with Unetbootin, and then reformat it from the installer.

---

### Post by Dr. C on 2010-10-25
> **ged25 said:**
> I have an old laptop on which I'd like to install a lightweight distro. My problem is that it doesn't have a cd drive and it cannot boot of a flash drive. How can I install it?

What are the specs? I assume it has a floppy drive. There are many GNU / Linux distributions that fit in one or two floppies. [http://www.linuxlinks.com/Distributions/Floppy/]("http://www.linuxlinks.com/Distributions/Floppy/") Now to create the floppies one can a use a GNU / Linux computer with a floppy drive.

---

