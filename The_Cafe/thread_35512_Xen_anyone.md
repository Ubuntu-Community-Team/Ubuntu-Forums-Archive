---
title: "Xen anyone?"
date: 2005-05-19
forum: The Cafe
---

### Post by deception on 2005-05-19
I bought an issue of LinuxFormat, a UK magazine for Linux users and abusers. It comes with a huge article on Xen - an OSS virtualisation program for Linux O/S's. VMWare but opensource. It boasts "huge speed increases over previous implimentations". Anyone ever gave it a shot? I might just for giggles.

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=deception]Anyone ever gave it a shot? I might just for giggles.[/QUOTE]


If you want to try it, I think the new Fedora and the new SUSE support it by default.

---

### Post by Xian on 2005-05-19
YaST doesn't install it by default, but it is included in the CD's/DVD.
The whole alternate kernel/system required to run Xen was a little heavy.

---

### Post by jdong on 2005-05-19
I didn't really like it that much, because much of the configuration still has to be tweaked by hand. Furthermore, you need to specify the amount of RAM to dedicate to VM's at bootup, making it VERY inflexible for experimenting.


If you have serious virtualization requirements, invest in a sound solution, like VMWare.

If you are playing around with virtualization for non-critical purposes, try qemu or UML or FAUmaching or other easier-to-manage emulators.


We really need to wait for Xen to mature and for distros to make BETTER, easier-to-use tools.

---

### Post by Xian on 2005-05-19
[QUOTE=jdong]We really need to wait for Xen to mature and for distros to make BETTER, easier-to-use tools.[/QUOTE]
Agree. YaST has a nice module to basically install a setup for Xen to boot into and thereby get the new kernel running, but from there it gets more tricky. It will be interesting to see what Breezy does with this application.

---

### Post by jdong on 2005-05-19
Let's also not forget Fedora. I sense Core 4 will be a VERY strong release. Preliminary reviews already shows it to be much faster than prior, and it's also getting Xen.

---

### Post by randy on 2005-05-19
If you're looking for something that comes preconfigured with Xen check out [http://cosi.clarkson.edu/xen](http://cosi.clarkson.edu/xen) .  It's a Debian based Xen distribution and has some of the basic support for Xen built in currently.

---

### Post by Xian on 2005-05-19
[QUOTE=randy]If you're looking for something that comes preconfigured with Xen check out [http://cosi.clarkson.edu/xen](http://cosi.clarkson.edu/xen) .  It's a Debian based Xen distribution and has some of the basic support for Xen built in currently.[/QUOTE]
*"Our first release Laura, is available here. Please be carefull using this image as it is currently in heavy development and is not considered stable. It may eat your system and then start doing bad things"*

Heh. :)

---

### Post by TravisNewman on 2005-05-19
Xen is NOT like VMWare, it's more efficient (or will be when it gets some more maturity under it's belt). Its paravirtualization, not just virtualization. See the Xen website for the differences ;)

---

### Post by jdong on 2005-05-20
[QUOTE=panickedthumb]Xen is NOT like VMWare, it's more efficient (or will be when it gets some more maturity under it's belt). Its paravirtualization, not just virtualization. See the Xen website for the differences ;)[/QUOTE]

I know, but VMWare's high-end products, like GSX server, do run very impressively. I was able to host four *gentoo* servers on a P4-2.4+HT and it ran very well.

---

### Post by deception on 2005-05-20
Well, seeing as I am just tinkering, nothing crucial, I'm going to install Xen on the desktop, will let you all know how it goes! 

If I'm not impressed I shall try out the other sugggestions kindly proposed by John  :)

---

### Post by randy on 2005-05-21
If your installing it on your Desktop machine and you have an agp video card you'll either have to install the testing distribution or wait for 2.0.6 to be  released.  They've had some problems with agp support that have been fixed in testing.  2.0.6 should be released soon though.

---

### Post by Burgundavia on 2005-05-21
[http://udu.wiki.ubuntu.com/Xen](http://udu.wiki.ubuntu.com/Xen) <-- Breezy and Xen, the goal

Corey

---

