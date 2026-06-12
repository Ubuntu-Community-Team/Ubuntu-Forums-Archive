---
title: "Ubuntu 9.04 Vbox Guest Additions"
date: 2009-04-05
forum: Virtualisation
---

### Post by AoA Linux on 2009-04-05
Can someone explain to me how to install the guest additions for Ubuntu 9.04.  I have the OS installed inside of my Ubuntu 8.10 and need to know how to get the GA installed properly? 

Thanks!

---

### Post by Perryg on 2009-04-05
> **AoA Linux said:**
> Can someone explain to me how to install the guest additions for Ubuntu 9.04.  I have the OS installed inside of my Ubuntu 8.10 and need to know how to get the GA installed properly? 

Thanks!

Info provided from the VBox web site:

Sasquatch wrote:
I see the problem. It doesn't know the 1.6 version of xserver. The beta, which was version 1.5.99 was still working. It checks for a version and that doesn't match the installed version. You might want to edit the file yourself and change the version check. You have to unpack the run file first.

More info for how to install it properly. First you need to extract the installer. So run VBoxLinuxAdditions-x86/amd46.run --target ~/ga (you need the destination folder first of course). Then check the install.sh file, on line 415, you will see this:

    15 1.5.99.* | 1.6 )


Now after the 1.6, add a .0. This is needed, because the version that is returned by X -version is 1.6.0, not 1.6.

After you've fixed the install script, run it like you would install the GA.run file. So sudo ./install.sh.

---

### Post by binbash on 2009-04-05
[http://www.ubuntu-inside.me/2009/03/howto-fix-virtualbox-guest-additions.html](http://www.ubuntu-inside.me/2009/03/howto-fix-virtualbox-guest-additions.html)

---

### Post by bodhi.zazen on 2009-04-06
9.04 in running 1.7.*

---

### Post by Perryg on 2009-04-06
> **bodhi.zazen said:**
> 9.04 in running 1.7.*

Are you sure?
I just did another check  (X -version) and mine still says 1.6.0
I update everyday to be sure that I don't miss anything.

---

### Post by bodhi.zazen on 2009-04-06
> **Perryg said:**
> Are you sure?
I just did another check  (X -version) and mine still says 1.6.0
I update everyday to be sure that I don't miss anything.

No, I may be mistaken ...

I was looking at this package :

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=xserver-xorg](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=xserver-xorg)

If I am in error, I apologize.

---

### Post by Perryg on 2009-04-07
Apologies are not necessary my friend,

I have really been trying to keep up with this and was wondering.  Everything I could find still showed 1.6.0.  I was hoping that you were in fact correct and wonder why I could not find or get it!

---

