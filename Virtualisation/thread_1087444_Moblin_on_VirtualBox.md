---
title: "Moblin on VirtualBox?"
date: 2009-03-05
forum: Virtualisation
---

### Post by CJ Master on 2009-03-05
Hello, Quick question for you guys :) Is it possible to run Moblin2 alpha on Virtualbox? Because whenever I try it, it shows that the kernal is missing something. Probably because I'm using a desktop computer. I don't have a laptop that I can use either.

I just want to try out that 5 second booktup. :D

---

### Post by CJ Master on 2009-03-07
Bump, I'd really appreciate any help. =]

---

### Post by codeM on 2009-03-12
Hey up,

To get it working on Virtualbox:
Download the DEVELOPMENT version of Moblin, not the regular version.
(For development iso from main Moblin.org page select "Build the next generation...." then "Download development images" from the menu on the right).

If you want additions:
As root:
    yum install kernel-netbook-devel.i586
    *restart*
Then install additions

Now, to get display working:
    Xorg -configure :1
    cp /root/xorg.conf.new /etc/X11/xorg.conf
    *restart*

... and Robert's your father's brother, as they say.

---

### Post by CJ Master on 2009-03-13
Yea, I did that. But right after I choose boot from the menu it spits out an error about me having the wrong kernal.

I assume that the Yum commmand is something to be run in moblin, right? If I'm supposed to run it beforehand, could you please specify a aptitude alternative? Thank you. :)

---

### Post by Biga_ on 2009-03-18
Turn on PAE/NX in the virtual machine settings (section "General", tab "Advanced", "Extended Features:").

---

### Post by Dedoimedo on 2009-03-18
I had issues with their live iso. I only managed to boot the vmware image they created. I had unsupported arch thingie.
Mrk

---

### Post by |Porsche on 2009-05-22
I didn't have any issued installing and running it under virtualbox 2.2.2 r46594.

---

### Post by ____ on 2009-06-16
I think that moblin only works with netbook cpus, i had the same error on my laptop. i think they should build a regular laptop version for an "instant-on" like os.

---

### Post by LordMarmite on 2009-06-17
had the same problem about using an "appropriate kernel", etc.

you need to change a couple of the virtual machine settings under the advanced tab (IO APIC and PAE/NX)

this should help out anyone else having the same issue
[http://www.to-tech.com/blog/2009/05/23/configuring-virtualbox-to-run-moblin-20-beta/](http://www.to-tech.com/blog/2009/05/23/configuring-virtualbox-to-run-moblin-20-beta/)

---

### Post by ____ on 2009-06-17
That worked, but now neither the mouse or the keyboard work.

---

### Post by Jose Catre-Vandis on 2009-06-17
> **codeM said:**
> ... and Robert's your father's brother, as they say.

Robert is actually my sister's husband, will that make a difference ?  :)


Can't get Moblin to finish boot, I get the syslinux screen, choose Boot then lots of boot up text then I get a pile of udevd-event errors then get dropped into a bash shell. I am told that there is a problem as follows: 
```
/init: line 337 917 illegal instruction  /bin/sleep/1
Bug in initramfs /init detected Dropping to shell
```

VBox 2.2.2 and MOblin alpha2-20090311

---

### Post by khughitt on 2009-09-10
> **____ said:**
> That worked, but now neither the mouse or the keyboard work.

Using the VMWare image worked for me (see [http://blog.bobpeers.com/2009/05/04/running-moblin-in-virtualbox/](http://blog.bobpeers.com/2009/05/04/running-moblin-in-virtualbox/)).

The mouse and keyboard still seem to occasionally lock-up, however.

---

### Post by zoomy942 on 2009-10-06
i am running moblin ubuntun remix in a VB and wow is it SLOW.  i dont understand why.  my XP vm's work great.  

anyone else notice this?

---

### Post by coolman98 on 2010-07-27
im trying it right now

---

