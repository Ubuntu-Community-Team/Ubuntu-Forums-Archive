---
title: "Galago UltraPro - Drivers"
date: 2014-10-08
forum: System76 Support
---

### Post by patrick_remmels on 2014-10-08
Hey there,
I received a Clevo W740SU (Galago UltraPro) with Windows 7 preinstalled.
As I plan on using ubuntu or linux mint and as I'm not very experienced in linux I don't know which drivers I need to install on my own.

The wiki page of System76 only tells me "System76 computers include all of the drivers required for Ubuntu".

Since I will install ubuntu or linux mint on my own I don't think that applies.
The only topic I found in this forum was concerning the Intel driver.

The Intel driver should be in the ubuntu repositories, how do I install it or will that be made on its own?

What about the rest as network/wifi, touchpad, USB3, audio, webcam, ..?

Thank you,
Patrick

---

### Post by patrick_remmels on 2014-10-08
I just found this website:
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

It seems like there is a package including all the necessary drivers.
As I am always curious: can someone tell me which drivers are included in this package?

---

### Post by monocell on 2014-10-08
I'm not using system76 customisations either and network, wifi, audio, webcam works out of the box. I'm not using ubuntu or mint but I believe both are more liberal with extra kernel modules than what I'm using, so you should be fine. The touchpad works but I hate all touchpads so I wouldn't notice if there was a problem there. Some of the function keys might not work either. In particular the monitor and airplane mode one.I have not dwelled into the contents of the system 76 stuff but I believe there are no drivers per se, but rather a python script running in the background working around some issues similar to the function buttons. Looking at the changelog might shed some light, or walk through the python script if you are super interested.

---

### Post by patrick_remmels on 2014-10-08
As far as I know this notebook is supposed to have good linux support so I want the things to work, the function keys as well. 

I tried to install these system76 drivers in a virtualbox but all it does is giving you one more option in the system preferences to install/update drivers.
As this isn't a system76 machine it won't let you go on istalling the drivers. I was hoping on getting some information what it installs this way.

Maybe there is a person here owning this particular notebook that can tell me..

---

### Post by monocell on 2014-10-08
Look at the install instructions from the arch-linux system 76 package. It mentions a file you have to edit to make it installable on a non system 76 laptop.Download the pkgbuild and look inside the .install file. I haven't actually tried this, but from the instructions it does look promising.[https://aur.archlinux.org/packages/system76-driver/](https://aur.archlinux.org/packages/system76-driver/)

---

### Post by patrick_remmels on 2014-10-09
> **monocell said:**
> Look at the install instructions from the arch-linux system 76 package. It mentions a file you have to edit to make it installable on a non system 76 laptop.Download the pkgbuild and look inside the .install file. I haven't actually tried this, but from the instructions it does look promising.[https://aur.archlinux.org/packages/system76-driver/](https://aur.archlinux.org/packages/system76-driver/)

Thanks for the reply, it did look quite promising.

But looking into I found that the main difference here is that they take a ubuntu package and want to make it work for Archlinux. One of the steps is faking the vendor and model ID to get the package to accept the computer as a System76 product. 
Taking the Archlinux thing now I have to somehow convert it back to a package usable by Ubuntu/Linux Mint which will be more work than faking the model ID.
At least that's how I understand it, as I said, I don't have a lot of experience with Linux and that's mainly logical analysis..

---

### Post by patrick_remmels on 2014-10-09
ok, so I found someone who helped me out to install the drivers. If anyone needs to know how just send me a message.

---

### Post by Thalarse on 2014-10-26
How has your galago been going? Mine has been having wifi problems. :/

---

