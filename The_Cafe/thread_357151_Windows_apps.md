---
title: "Windows apps"
date: 2007-02-09
forum: The Cafe
---

### Post by Sanus Compleo on 2007-02-09
I think there is already one called red wine, it allows you to run windows apps on ubuntu, but it is in a format that ubuntu cannot read.  Does anyone know where to get a program that allows you to run windows and other os applications on ubuntu?

---

### Post by mykalreborn on 2007-02-09
[http://winehq.org/](http://winehq.org/)
and if you don't want to install it manually, you can go here:
[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by divague on 2007-02-09
Install wine:

edit your /etc/apt/sources.list file and add this repos

## WineHQ - Ubuntu 6.10 "edgy eft"
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

then in a terminal type this:

$wget [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)
$gpg --import 387EE263.gpg
$sudo apt-key add 387EE263.gpg

then:

$sudo apt-get update
$sudo apt-get install wine

to run and .exe file just type

$wine *name*.exe

---

### Post by ola on 2007-02-09
Hi and welcome to the Ubuntu forum!

There are several different methods on running Windows and Windows programs in Ubuntu (or other Linux distributions).

You mentioned Wine which is an implementation of functionality needed to run programs in Windows for Linux. You can see [http://www.winehq.com/](http://www.winehq.com/) for more information about Wine.

Then there is CrossOver which is an "improved" version of Wine. It costs $39.95 and is supposed to work really well. Check if the software you intend to run is supported at their web site: [http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

Both Wine and CrossOver is geared towards running Windows applications in Linux. 

If you want to run a complete installation of Windows in Linux you could check out VMware which is a virtual machine that allows you to run a complete Windows installation in Linux. They have a trial version of VMware Workstation which you can use to create the VMvare image (your installation of Windows) and then you can use the free VMware Player to run your installed Windows in Linux.

There are other alternatives, but these are the once I'm most familiar with. Good luck!

Best regards,

Ola

---

### Post by Sanus Compleo on 2007-02-09
Well, I don't want to emulate windows, that is why is switched to Ubuntu, I think automatix should work, but I would like to know more about some of these programs, like are there any that are free, and work on most programs?  Thank you guys for helping me out, this is awesome that you would od this for me.  I think I will stick with Ubuntu for a long time.

---

### Post by TheRingmaster on 2007-02-09
> **Sanus Compleo said:**
> Well, I don't want to emulate windows, that is why is switched to Ubuntu, I think automatix should work, but I would like to know more about some of these programs, like are there any that are free, and work on most programs?  Thank you guys for helping me out, this is awesome that you would od this for me.  I think I will stick with Ubuntu for a long time.


Most software for ubuntu is free (gratis & libre):KS

---

