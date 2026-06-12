---
title: "Black screen at login"
date: 2013-02-03
forum: Ubuntu Development Version
---

### Post by shaneo1 on 2013-02-03
Since I updated Raring last week, I an no longer able to see the lightdm login screen and just left with a flashing _ cursor in the top left of the screen, I am not able to tty either.  I rebooted and opened up recovery mode and removed nvidia drivers in the hope that it would default to the noueuv ?? drivers, but it does not, however it does allow me to login via tty.

I am not stuck what should I do next? is there a log file I need to look at to see what the issue is?

Any assistance would be greatly accepted.

Information I can get: 
kernel 3.5.0-18-generic

thanks

Shane

---

### Post by ft_ on 2013-02-03
it's odd that your kernel is still Quantal's.
I would first check that linux-image 3.8 is installed and update-grub if 3.8 is not present in menu.

---

### Post by Harry33 on 2013-02-03
> **ft_ said:**
> it's odd that your kernel is still Quantal's.
I would first check that linux-image 3.8 is installed and update-grub if 3.8 is not present in menu.

I doubt it is a raring setup at all.
The kernel meta files would have installed the latest kernel there is (3.8 rc 6).

---

### Post by shaneo1 on 2013-02-03
how do you suggest I update the kernal version.

I had to use 12.10 to install ubuntu as I was having issues with the dailies for 13.04, then I upgraded. but still lingering on 3.5.0-18-generic

---

### Post by shaneo1 on 2013-02-03
I have tried

sudo apt-get upgrade && sudo apt-get dist-upgrade

with no joy.

I have also checked that the sources.list is for raring.

---

### Post by shaneo1 on 2013-02-03
I now have the latest kernel 3.8.0-4-generic installed and running, the issue was that alsa-hda-dkms package was holding it back.  It was a Raring install, but it still hasn't fixed my black screen issue where X fails at login.

---

### Post by Harry33 on 2013-02-04
> **shaneo1 said:**
> I now have the latest kernel 3.8.0-4-generic installed and running, the issue was that alsa-hda-dkms package was holding it back.  It was a Raring install, but it still hasn't fixed my black screen issue where X fails at login.

If you are not using an old nvidia graphics card, you should install the latest nvidia drivers back.
Please check wich version is built for your graphics card from manufacturers web site:
[www.nvidia.com](www.nvidia.com)

---

### Post by grahammechanical on 2013-02-04
I am running a 13.04 install that was converted from 12.10 at the start of the development cycle. The Quantal kernel 3.5.0-17 is still in my boot folder. It will remain there until I remove it.

This install has received the 3.7.0 series. But I could not get a desktop with 3.7.0-1 through to 3.7.0-4. This sometimes happens. I am not having problems with 3.8.0-0 through to the latest 3.8.0-4. But sometimes some of us do have these issues.

It should be possible to use Nouveau. May I suggest that you boot into that 3.5.0-18 kernel as you seem to get a desktop with that kernel and then go to Software Sources>Additional Drivers tab and see if you get activate the Nouveau Driver or one of the others.

There has been issues with proprietary drivers for many months. If we install and tick Third Party Software we get the proprietary driver and possibly a broken desktop. I always install without pulling in thrird party software. Then I most definitely get Nouveau.

At present I have 7 drivers to choose from. Nvidia-310 (proprietary, tested) works for me with Linux kernel 3.8.0-4.   That or one of the others may work for you. I do find Nouveau acceptable.

At that flashing cursor you could try

```
startx
```

> In simplest terms the startx command is responsible for launching the X session on your computer. The X session is the underpinnings of the graphical desktop

Regards.

---

