---
title: "VirtualBox USB...is the OSE good enough?"
date: 2008-04-23
forum: Virtualisation
---

### Post by scamper_22 on 2008-04-23
Hi,

I'm trying to get my USB working in Virtualbox.  I've followed most of the advice I've found, but nothing.

One of the things I've read is that VirtualBox OSE does not support USB.  Is this true and thus all the posts are referring to the commercial version of vitrualbox?  If so, I don't mind paying for VirtualBox commercial edition...but where do I purchase it?  The virtualbox site doesn't seem to have anything?

I can't find any references to USB in the VirtualBox OSE (anywhere in the GUI)

Any Ideas?

Y

---

### Post by Whiffle on 2008-04-23
You don't need to pay for it, there is the non open source edition that supports usb (and works very well) [http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by scamper_22 on 2008-04-23
Thanks,

Seems so obvious now :P

Anyways, I've upgraded to hardy heron and the only version I can see if for 7.10.  Would this still work?

---

### Post by Whiffle on 2008-04-23
I'd say theres a good chance it wouldn't due to changes in the kernel and such, but if you're patient I'm sure there will be another version soon after hardy is released.  I you need it yesterday, then you could get the generic linux installer and use that.

---

### Post by scamper_22 on 2008-04-23
sweeet.  works great.

---

### Post by toorima on 2008-04-24
I run hardy and use the gutsy version, works very well, just add the following to /etc/apt/sources.list

## Virtualbox non-OSE
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

---

