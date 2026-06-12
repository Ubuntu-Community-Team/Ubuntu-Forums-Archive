---
title: "Xen setup on ubuntu 10.4, or maybe not?"
date: 2010-05-08
forum: Virtualisation
---

### Post by ddCool on 2010-05-08
Hey everyone,

I've heard of Ubuntu A LOT in the past, but I've installed it on a virtual machine only recently.

Being fed up with Win stability and other issues (from XP through Vista and eventually 7), I've decided to try Ubuntu.
Meanwhile I'm getting to know it, but when I thought what an OS should be like, Ubuntu is what I had in mind, boy am I having a second childhood with it :).

But here's the problem:
I'm a web developer and designer, and the software I use for design doesn't work with Ubuntu. Many will say go open source, but that is not an option. Years of experience, workflow, tools you're used to, plus industry standards - can't do that.

So I've done some reading and found that the olny way to run Adobe soft is to run it on virtual machine. OK, but Photoshop and other programs need direct access to the video card, plus they are memory-hungry.
I thought to go with Xen, so I can switch to Ubuntu and still have my Graphic software running its full potential on Win.
Ow and it needs to be 64bit!

Can anyone please point me in the right direction with this?
Or maybe there's a better solution (except open source alternatives)?

Many thanks in advance!
Dean

---

### Post by stephanhughson on 2010-05-08
Hi,

So it sounds like you have Ubuntu (the desktop version) and want to run some Windows applications? Xen isn't included in Ubuntu anymore (the major distributions are moving to KVM instead), but for what you need, I would suggest Virtualbox OSE instead anyway.

I'm pretty sure that will do what you need. I've used it in the past, it's very good and should cope fine with 64 bit Windows as far as I know.

Let me know if that helps or not.


Editing...
Just realised I didn't answer the bit about the direct access to the video card. I think only the operating system you are running will have direct access to the graphics card. It is possible to "pass through" devices to virtual machines, but I don't think it would be possible for something like a graphics card. It could still work quite nicely...

---

### Post by ddCool on 2010-05-09
Thanks :)

This "pass-through" is exactly what I need and why I decided to try Xen.
I've read about it, and it is possible to passthrough to the VGA, I even saw videos of people running heavy 3D stuff.

---

### Post by stephanhughson on 2010-05-09
I'm not sure Xen will work out for you, Ubuntu have basically dropped it for KVM instead. KVM the way I use it is more of a server solution. I use VNC to access the actual screen, so that might not be great for your graphics stuff!

Virtualbox is probably best for you, but I'm not sure if it supports what you need. You could ask here: [http://forums.virtualbox.org/](http://forums.virtualbox.org/)

Virtualbox is a nice GUI application. KVM does have a GUI frontend, but I'm pretty sure it uses VNC to access the screen.

Maybe dual boot is best? Or just having two computers! To be honest...:confused:

---

### Post by ddCool on 2010-05-09
I've checked with many virtualization solutions, and the only one to provide VGA passthrough is Xen. This passthrough feature is crucial for graphic apps.

Dual boot is OK if u play games, but in graphic design and web design workflows, that will be very frustrating. It kind of kills the point of switching over, and don't get me wrong I really really want to switch to Ubuntu.

Thanks anyway.

Any advice and suggestions are highly appreciated :)

Many thanks in advance.

If there's anyone with the sufficient knowledge, please help me with this.

---

### Post by ve2abo on 2010-08-08
This post is not exactly new but a few month is still recent enough for you not yet givin up on this project....

You may want to visit this page:

[Set up Ubuntu 10.04 Server PV DomU at Xen 4.0 Dom0 (pvops 2.6.32.12 kernel) Dom0 on top of Ubuntu 10.04 Server « Xen Virtualization on Linux and Solaris]("http://bderzhavets.wordpress.com/2010/04/24/set-up-ubuntu-10-04-server-pv-domu-at-xen-4-0-dom0-pvops-2-6-32-10-kernel-dom0-on-top-of-ubuntu-10-04-server/") 

I did manage to install Xen 4.01 rc5 over Ubuntu 10.04 Desktop 64-bits following this page. I'm now trying the vga passthrough, based on this page:

[http://wiki.xensource.com/xenwiki/XenVGAPassthrough?highlight=%28passthrough%29|%28vga%29]("http://wiki.xensource.com/xenwiki/XenVGAPassthrough?highlight=%28passthrough%29%7C%28vga%29") 

but so far i've been unlucky. But the important thing to keep in mind is that your hardware is the key in this "feat" because not all graphics card can do this "out of the 'download' " of xen.

Good luck !!

---

