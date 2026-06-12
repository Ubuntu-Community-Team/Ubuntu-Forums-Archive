---
title: "Which nVidia driver do you use?"
date: 2007-10-03
forum: The Cafe
---

### Post by master_kernel on 2007-10-03
I am conducting even MORE research for [KernelCheck]("http://kcheck.sourceforge.net") and I need to include an option to autoinstall nVidia drivers (legacy and non-legacy). Please post the way you installed it (website binary or Ubuntu repositories). Thank you!

---

### Post by -grubby on 2007-10-03
non legacy nvidia from the restricted-drivers-manager

---

### Post by screaminj3sus on 2007-10-03
I just use the restricted-manager; easy, convenient, and works great.

---

### Post by master_kernel on 2007-10-04
> **screaminj3sus said:**
> I just use the restricted-manager; easy, convenient, and works great.
That would fall under Ubuntu repos.

---

### Post by FuturePilot on 2007-10-04
My laptop is running the Legacy driver (9639) from the Gutsy repos. But I have a feeling that may change soon because the latest Legacy driver (9643) seems to have fixed the black window bug which has haunted my laptop. 
My desktop is using the Legacy 9631 from Feisty's repos. I could use the newer one (9755) but I figured better not. Why fix what isn't broken? But I plan on using the 100.14.19 drivers that are in Gutsy's repos when I install Gutsy.
My other laptop is using the 100.14.19 driver from Nvidia's site due to the fact that none of the drivers in Feisty support the card.

---

### Post by Sunflower1970 on 2007-10-04
I use one of both. Legacy on one computer and current driver on the other from the Ubuntu repositories.

---

### Post by Dimitriid on 2007-10-04
I use the driver envy installs. I tried a few moments ago to uninstall it. x crashed afterwards of course. I tried to reconfigure x ( dpkg-reconfigure xserver-xorg ) and I got x back for some reason metacity would not start, and under 'restricted drivers manager' I did not had the option to install Ubuntu's default restricted driver manager. So I guess I have to do something else to remove Envy and have only
Ubuntu's default restricted ( it shows I have the restricted now but I think it installs a more up to date one ) 

I'll wrestle with this more later.

---

### Post by ~LoKe on 2007-10-04
I use Envy.  Too much time spent trying to get the drivers working consistently myself, it's easier this way.

---

### Post by master_kernel on 2007-10-07
I think Envy uses the binary driver from the nVidia site.

---

### Post by CulleyS on 2007-10-08
I'm using the driver that came with NVIDIA-Linux-x86_64-100.14.19-pkg2 from the NVIDIA site.

Running Ubuntu gutsy (development branch), kernel 2.6.22-13-generic on an AMD 64 processor.  Gfx card is GeForce 8600GT.

With it, I've managed to get some stuff to work, but not everything. :)  Dual monitors now works for me.  As I mentioned in another post, couldn't get dual monitors to work using the restricted driver manager method.  Haven't tried  Envy.

---

### Post by OffHand on 2007-10-08
I use the binary from the Nvidia website....

---

### Post by wdo_will on 2007-10-08
I feel guilty for doing it, but I use the non-free driver from the Ubuntu repos.

---

### Post by ssam on 2007-10-08
nv.

the nvidia one is too unstable (some issue with 100.14.19 + dual core + 7300 cards) [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/145112](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/145112)

i have tried the nouveau driver, and it is coming along nicely.

---

### Post by cogadh on 2007-10-08
I use the nvidia-glx-new package from the repositories (9755 driver). That isn't the default Nvidia driver from the repositories (9633 driver) and certainly isn't the legacy driver, so I voted "other".

---

### Post by master_kernel on 2007-10-29
Any way to get non-legacy working with 2.6.23?

---

