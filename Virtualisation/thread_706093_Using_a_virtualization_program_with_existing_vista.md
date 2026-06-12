---
title: "Using a virtualization program with existing vista install (in Gutsy)?"
date: 2008-02-24
forum: Virtualisation
---

### Post by Mad_Gouki on 2008-02-24
I have Gutsy x86, and windows Vista installed on my laptop.  I have been looking at virtualization programs for running Vista inside of Ubuntu, but they all seem to require an image of the os to be used.  Are there any virtualization programs that support use of the physical install on the hard drive, or do they all require a virtual image to be made?  I also have seen where it is possible to create a virtual machine image from an existing install on a hard drive, or create one with a fresh install, are there any other options?

---

### Post by toa on 2008-02-24
> **Mad_Gouki said:**
> I have Gutsy x86, and windows Vista installed on my laptop.  I have been looking at virtualization programs for running Vista inside of Ubuntu, but they all seem to require an image of the os to be used.  Are there any virtualization programs that support use of the physical install on the hard drive, or do they all require a virtual image to be made?  I also have seen where it is possible to create a virtual machine image from an existing install on a hard drive, or create one with a fresh install, are there any other options?

I've tried that, but the steps taken were supposed to be for XP, it will defnitely screw the system, having Ubuntu's virtual system run and existing Vista installed, with all those processes, so what happens you log out from ubuntu and vista is running, or a sudden system shutdown... ( i thought about it) but physically its not recommended.

Virtual is more safe... or the classic dual booting.

..

---

### Post by Mad_Gouki on 2008-02-24
Thank you, now that I think about it, XP would go psycho sometimes after the hardware changed and give all sorts of errors, I can only imagine how bad I could mess up my vista install by putting it in a VM  :shock:  [COLOR=LemonChiffon](or by running it normally)[/COLOR]

---

### Post by jimcooncat on 2008-02-24
You may want to consider colinux. [http://www.colinux.org/](http://www.colinux.org/)

oops, sorry! Vista's not supported.

---

### Post by mbsullivan on 2008-02-24
Hey,

It seems it's possible,and actually pretty slick. You'll probably find the best support with VMWare. Check it out [here]("http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition").

Mike

---

### Post by mbsullivan on 2008-02-26
Mad_Gouki,

Did you have any progress? If so, does it work well? I ask because I'm interested but **WAY** too lazy to try it myself.

Mike

---

### Post by bodhi.zazen on 2008-02-26
Booting a physical partition with VMWare is Beta at best and can cause major problems.

With that warning , see the sticky at the top of this forum.

---

