---
title: "System76 Laptop Questions"
date: 2014-01-12
forum: System76 Support
---

### Post by Sean_Chen on 2014-01-12
Dear Supporters

1. The graphic card switching tech are not suitable for linux OS, so System76(Bonobo Extreme) solve this problem by using just one Graphic Card(nVidia GeForce GTX, no second on chip grapphic card), am I right?

2. The System76 laptop said it has optimized for ubuntu OS, I totally know how to install ubuntu, but is there any hard for ordinary people like me to use this optimization after I install Ubuntu? For personal reasons, I need to use 3 different OS at one Laptop, so I will definitely re-install Ubuntu on my own System76 laptop, what I worried about is that may be some special process need to be done when we installing ubuntu.

---

### Post by porcini_m.2 on 2014-01-12
> **Sean_Chen said:**
> 
2. The System76 laptop said it has optimized for ubuntu OS, I totally know how to install ubuntu, but is there any hard for ordinary people like me to use this optimization after I install Ubuntu? For personal reasons, I need to use 3 different OS at one Laptop, so I will definitely re-install Ubuntu on my own System76 laptop, what I worried about is that may be some special process need to be done when we installing ubuntu.

The only special thing to do on installation is to install extra system76 drivers - these are available through a PPA - see the system76 website for instructions.

---

### Post by Sean_Chen on 2014-01-13
If this PPA is easy to be done by amateurs, that would be cool~~

while is that means there is no extra system76 drivers for other linux distri like Fedora and Arch?

---

### Post by hawkmage on 2014-01-15
Don't know about Arch but if you add the Fusion Repo to Fedora you can install the Nvidia card driver through yum.  I am currently testing Fedora 20 on a Bonobo with the GeForce GTX 780M

---

### Post by stealth_anon on 2014-01-17
I have a BonoboEXtreme, removed Ubuntu 13.10 and installed Manjaro Openbox (Archbased) no issues at all with sys76 drivers, you can find them within the AUR via the 'yaourt' command.

It works like a charm even with Xubuntu, Mint and Fedora 

\\:D/

---

### Post by joe4ska on 2014-01-18
It's worth mentioning that System76 uses their own bios which are also optimzed for Ubuntu and therefore GNU/Linux so no matter which distro you go with you'll have that advantage. You don't need to add a PPA to get the latest driver, but it will only work for official Ubuntu variants. (and they have Windows drivers if you must.)

[The System76 driver]("http://knowledge76.com/index.php/System76_Driver") | [Bonobo Knolege76 Support Page]("http://knowledge76.com/index.php/Category:Bonobo")

I've dual booted serveral GNU/Linux distros and distro hopped several dozen times. You can always optimize the system on your end, I turn to YouTube for tutorials and tips.

---

### Post by ChiefWOTJ on 2014-01-20
> **Sean_Chen said:**
> If this PPA is easy to be done by amateurs, that would be cool~~

while is that means there is no extra system76 drivers for other linux distri like Fedora and Arch?

The PPA is very easy.  It's a sudo add-apt-repository command, then update and install.  I currently have openSUSE installed on my Gazelle Professional, and while there is no "driver" package available per se, I added the line 'acpi_backlight=vendor' to my boot parameters, and the brightness keys work just fine.  I would imagine the same thing would work for Fedora and/or Arch, but I've not tried it.

---

### Post by ~cyrus~ on 2014-01-23
> **Sean_Chen said:**
> If this PPA is easy to be done by amateurs, that would be cool~~

while is that means there is no extra system76 drivers for other linux distri like Fedora and Arch?

I have Arch KDE running on my Bonobo Extreme ( bonx6 ) with the nVidia GeForce GTX 670MX and couldn't be happier. 

You need to install the nvidia-304xx package, available in the official repositories. As you are on 64-bit you also need 32-bit OpenGL support, and you need to install the equivalent lib32 package from the multilib repository which is lib32-nvidia-304xx-utils. Take a look at the [Xorg]("https://wiki.archlinux.org/index.php/Xorg#Driver_installation") page in the Wiki.

---

