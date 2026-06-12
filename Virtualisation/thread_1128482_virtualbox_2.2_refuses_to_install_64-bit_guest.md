---
title: "virtualbox 2.2 refuses to install 64-bit guest"
date: 2009-04-17
forum: Virtualisation
---

### Post by brandon88tube on 2009-04-17
I'm running Ubuntu 8.10 64-bit and have installed virtualbox 2.2 amd64, but when I try to install a 64-bit guest os it refuses and says I only have x86 hardware. Can someone help me so I can get a 64-bit os up and running?

---

### Post by bodhi.zazen on 2009-04-17
I have this problem also. It seems to depend on the exact CPU.

On one machine I can run 64 bit guests, you need to select a 64 bit guest when you set up the guest (VBox seems to default to 32 bit and is not "smart" enough to change to 64 bit support when it boots a 64 bit OS, too bad really).

On my other machine , still no joy with 64 bit guests despite running a 64 bit host.

If you can not get it running via the menu, I suggest you post on the VirtualBox forums. Be sure to specify the make / model of your CPU.

---

### Post by brandon88tube on 2009-04-17
> **bodhi.zazen said:**
> I have this problem also. It seems to depend on the exact CPU.

On one machine I can run 64 bit guests, you need to select a 64 bit guest when you set up the guest (VBox seems to default to 32 bit and is not "smart" enough to change to 64 bit support when it boots a 64 bit OS, too bad really).

Where is the option to select 64-bit guest? I must have missed that somewhere.

---

### Post by bodhi.zazen on 2009-04-17
When you make a new guest, as you go through the set up, you select the OS from a pull down list.

There should be, for example, Ubuntu and Ubuntu 64 bit.

---

### Post by brandon88tube on 2009-04-17
Really? I don't see that option at all. Just gives me the Linux > Ubuntu and none of the choices have 64 in them.

---

### Post by bodhi.zazen on 2009-04-17
Open virtualbox

Select your machine on the Left.

In the "Details" tab, on the right, click on general.

In the "Basic" tab -> Operating system -> Linux.

Version - Select "Ubuntu 64 bit"

Save and boot ;)

---

### Post by brandon88tube on 2009-04-17
> **bodhi.zazen said:**
> Open virtualbox

Select your machine on the Left.

In the "Details" tab, on the right, click on general.

In the "Basic" tab -> Operating system -> Linux.

Version - Select "Ubuntu 64 bit"

Save and boot ;)

Yeah, it doesn't give me the option of selecting 64-bit.

---

### Post by bodhi.zazen on 2009-04-17
Yes, this is the way it is on my "broken" 64 bit processor.

[quote]# uname -a
Linux 2.6.27.21 #1 SMP Mon Mar 23 23:08:10 EDT 2009 **x86_64 x86_64 x86_64 GNU/Linux**[/code]

And on this same 64 bit OS , no option for 64 bit guest in Virtualbox.

So, this is a bug with virtualbox and you should report it as such to the Virtualbox developers.

---

### Post by brandon88tube on 2009-04-18
I've decided to sign up and ask on the virtualbox forums before I report it as a bug. I think it would be better to ask there before reporting as a bug if it technically is not.

---

### Post by brandon88tube on 2009-04-18
Turns out my AMD processor doesn't support AMD-V, which VirtualBox requires to have a 64-bit guest operating system. That might be your problem as well, but that is really lame that I have a 64-bit processor and I can't even virtualize a 64-bit OS.

---

