---
title: "Is Virtualbox stable?"
date: 2013-08-10
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-08-10
I am thinking about upgrading my raring kernel to 3.11rc5 when it comes out (my guess is that is tomorrow) as well as my nvidia driver (via nvidia's run file)
this will break the stock virtualbox so i wanted to know if the virtualbox in saucy is stable

Edit:
i was not able to get the nvida driver to compile on linux 3.11rc5 from nvidia under raring

---

### Post by John_McCourt on 2013-08-13
This is a test version... Nothing is stable. Anything can change at any moment.

---

### Post by fjgaude on 2013-08-13
It is for me and my Intel-based video... very stable and fast!

---

### Post by xeizoo on 2013-08-14
I managed to install the latest Windows 8.1-build in Virtualbox under Saucy(3.11-RC5, Gnome-shell, Nvidia), works fine with guest additions and 2D/3D-accelleration ticked. Seems pretty stable to me ...

---

### Post by Aenima99x on 2013-08-15
Can anyone verify if the seamless mode issues are still present in 13.10? 
This is the issues I'm referring to - [http://askubuntu.com/questions/316501/windows-7-virtualbox-guest-in-seamless-mode-has-bottom-clipped-off-in-ubuntu-13](http://askubuntu.com/questions/316501/windows-7-virtualbox-guest-in-seamless-mode-has-bottom-clipped-off-in-ubuntu-13)

---

### Post by PJs Ronin on 2013-08-15
Still an issue for me Aenima99x.   Only on Unity.   If I run the VM under Gnome or Xfce I don't have the problem.   I'm also having the same problem in Saucy.   Apart from that, VB (Win 7 Pro guest) is very stable for me in Raring and Saucy.

---

### Post by PJs Ronin on 2013-08-30
> **Aenima99x said:**
> Can anyone verify if the seamless mode issues are still present in 13.10? 
This is the issues I'm referring to - [http://askubuntu.com/questions/316501/windows-7-virtualbox-guest-in-seamless-mode-has-bottom-clipped-off-in-ubuntu-13](http://askubuntu.com/questions/316501/windows-7-virtualbox-guest-in-seamless-mode-has-bottom-clipped-off-in-ubuntu-13)

Not sure if this thread is dead or not, but I have now upgraded to 13.10 and today noticed there was a virtualbox update.   Consequently, the Win 7 VM no longer has the bottom panel clipped.

---

### Post by ventrical on 2013-08-31
I installed Virtual Box on a system about a week ago. When I upgraded 2 days ago I had all kind of vb kernel message errors (I hadn't even run vb yet) !! Then yesterday that install crashed completely (mind you I was doing some serious overclocking on that system).. but only vb was reporting errors.

---

### Post by Russ Herman on 2013-08-31
Works fine here on client Saucy with 32-bit 3.11.0-4-generic kernel. Guest Additions installed as well, with invalid complaints about lack of kernel headers. Make sure you have dkms installed if this is the first time you're doing anything with drivers.

---

