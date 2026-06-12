---
title: "Virtualizing OS X with QEMU?"
date: 2007-11-27
forum: Virtualisation
---

### Post by xMemphisx on 2007-11-27
I have an intel-based copy of OSX that i want to run virtually in Ubuntu, but when i try to boot, it looks like it will be successful and then it says there's an error with the ACPI, and it asks to restart the computer. How can i get this working?

---

### Post by dyous87 on 2007-11-28
I would also be really interested in getting this working perhaps with virtualbox. It would be interesting to run leopard on a virtual machine. Is this in anyway possible?

---

### Post by sceo on 2008-01-22
Also interested here.  For one, I would try running kvm (qemu) with the -no-acpi option, to disable it.  If you've already figured it out, please post back with your findings.

---

### Post by DeadZedz on 2008-03-09
I'd also like to run my intel osx on ubuntu; preferably in qemu
There is a intel mac qemu project here but Ihavent tried it [http://alex.csgraf.de/self/?qemu/](http://alex.csgraf.de/self/?qemu/)

---

### Post by Steveway on 2008-03-09
Afaik running OSX on a Virtualization-program is against their EULA.

---

### Post by scottro on 2008-03-09
Folks, please keep what steveway says in mind.  It means that if someone from Apple comes across this thread, they can complain, make like difficult and all that good stuff.  

Apple does not allow OS X to be run on non-Apple software.   I believe MS tried doing the same with Vista (you could only run it in an MS virtual machine or something similar) but changed their minds. 

I'm sure it's best if we make an effort to not advocate something against a manufacturer's EULA on these forums.  Unfortunately, Apple's user base isn't likely to make enough of a complaint to get Apple to change their policy, imho.  <shrug>.

---

### Post by erichmj on 2008-03-10
I just want to point out that NOT everyone is bound by the terms of the EULA for OS X. There are some countries and states that limit restrictions that Apple can place on a product. In some countries you are legally entitled to run OS X on any hardware you want so long as you own a license to it.

---

### Post by stmiller on 2008-07-27
Right now it is impossible to virtualize OS X without modifying the OS X kernel. Also you would have to emulate EFI. Also you would need intel hardare- AMD would probably not work well. Anyways it is quite a hack to do; you cannot simply pop in a DVD and start qemu....

see: osx86project

---

### Post by davewantsmoore on 2008-10-15
sigh... i'm, getting sick of all this legalesque talk... the bootom line is:

virtualizing OSX client version - against EULA

virtualizing OSX server ontop of mac hardware - fine

virtualizing OSX server ontop of non-mac hardware - debateable

Doing whatever you want when you live in a country that doesn't recognize the EULA - priceless!

---

I am very interested (and frustrated) to find a way to run OSX server virtualised ontop of Linux.

I get the feeling right now that it's only possible in vmware (but not ESX).  Comments?

Can anyone direct me to a howto/forum where I can learn the tricks to getting OSX server working on vmware host?

Are the any other virtualisation archs that are close to having this working?

Thanks.

---

### Post by akand074 on 2010-12-17
> **carolinason said:**
> bottom line is Apple Mac OS X is a load of crap!

I love how you had to bring a two year old thread back to life just to say that. Because it made me chuckle I'll give you a +1.

---

### Post by JaradT on 2010-12-18
> **Steveway said:**
> Afaik running OSX on a Virtualization-program is against their EULA.

Not if you're running on Apple hardware.
As long as you have Apple-labelled hardware, you can run OS X as a virtual machine in Windows, Linux or even OS X. :p

---

### Post by scottro on 2011-01-02
Well, since we've raised this thread from the dead, sort of anyway, it's now become relatively easy to install either a VMware image on VMware-player or install on VirtualBox from an actual Snow Leopard CD.  

As I'm still not sure of the legality, at least in the US, I'm not going to post links, but do a search for something like OSX virtualbox dinesh and it will come up.

---

### Post by wrapman on 2011-09-08
Oh look! Two years after you!

---

