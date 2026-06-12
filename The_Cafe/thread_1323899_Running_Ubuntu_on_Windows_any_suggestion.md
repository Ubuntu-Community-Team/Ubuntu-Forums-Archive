---
title: "Running Ubuntu on Windows: any suggestion?"
date: 2009-11-12
forum: The Cafe
---

### Post by gjatute on 2009-11-12
Hi! I'm not an absolute beginner, but I don't consider myself a real expert... So I would  like to ask a suggestion :-)

I found myself in a weird situation: I started a PhD and they don't allow me to partition the computer I have at work... No way I'm going to use Windozz, so I was wondering what's the best option to run Ubuntu under Windows. Should I install VirtualBox and install on that a regular Ubuntu? Should I use Portable Ubuntu? Or should just use a USB distribution?

Suggetions are welcome: it's the very first time I have this kind of issue...

By the way: have a nice day!

---

### Post by SunnyRabbiera on 2009-11-12
Virtualbox is a good idea

---

### Post by pwnst*r on 2009-11-12
> **SunnyRabbiera said:**
> Virtualbox is a good idea

agreed.  vbox is a great idea.  post if you need assistance with this, but lots of great guides and quite easy to do.  don't forget to add guest additions to run seamlessly between windows/ubuntu.

---

### Post by BenAshton24 on 2009-11-12
wubi is what you're looking for, [http://wubi-installer.org/](http://wubi-installer.org/)

no partitioning needed :)

---

### Post by pwnst*r on 2009-11-12
> **BenAshton24 said:**
> wubi is what you're looking for, [http://wubi-installer.org/](http://wubi-installer.org/)

no partitioning needed :)

NO NO NO, wubi sucks

---

### Post by mmix on 2009-11-12
> I started a PhD and they don't allow me to partition the computer I have at work

IIWY, format the HDD, install fedora 12, qemu-kvm, libvirt, virt-manager and

windows 7 university discount version($30). 

i.e. window 7 virtualization on Fedora 12.

---

### Post by gjatute on 2009-11-12
thank you very much! As soon as the new machine arrives I'll start playing around

---

### Post by BenAshton24 on 2009-11-12
> **pwnst*r said:**
> NO NO NO, wubi sucks

Care to extrapolate? How exactly does it suck?

---

### Post by underquark on 2009-11-12
My workplace is very restrictive (CDRW and USB write are disabled on all machines) but I have Xubuntu on a 1GB stick. Just enter the BIOS and re-order the boot options so that USB is before HDD.  Take the stick with you when you use a differnet machine.  See the various threads about creating a persistent USB disk e.g. [this one](https://wiki.ubuntu.com/LiveUsbPendrivePersistent).
 
Or bung in a small (i.e. cheap) 2nd hard drive and just act stupid if they find out :).

---

### Post by forrestcupp on 2009-11-12
> **pwnst*r said:**
> NO NO NO, wubi sucks

Wubi sucks compared to a real installation.  But I think in this situation, it's the way to go.  Wubi would be much better than virtualization.  And you can just uninstall it from the Control Panel like any other program.

BTW - Isn't a Wubi option still officially available on the Ubuntu CD?  You shouldn't have to download the installer, unless they did away with it in the newer versions.

---

