---
title: "Ubuntu guest vs win7 guest"
date: 2009-07-01
forum: Virtualisation
---

### Post by np0731 on 2009-07-01
ok so i have the new dell studio 1555 with the ati 4570 (256mb), 2.2ghz core 2 duo, and 4 gb ram.

im trying to decide between to things.

do i run Jaunty inside Windows 7, and if so, how much RAM/Video Memory should i allocate to it?

or do i run Windows 7 inside Jaunty, and if so, same questions, but also, will the sound work in the Jaunty ISO from [http://linux.dell.com/wiki/index.php/Ubuntu_9.04](http://linux.dell.com/wiki/index.php/Ubuntu_9.04)?

---

### Post by lykwydchykyn on 2009-07-01
I assume by "running $OS inside of $OS" you mean virtualization?

I think it really depends on what you intend to use each one for, and how comfortable you are with Ubuntu.

If we're talking about the "free" windows 7 RC, then I would definitely virtualize, because when the trial runs out you're going to be totally locked out of your machine.  OTOH, if you run Ubuntu as the host OS, then you can still use your machine a year from now.

If you need direct hardware access for windows in order to play games, then I'd recommend dual-booting.

---

### Post by np0731 on 2009-07-01
what about resource allocation?

im going to virtualize win7 inside ubuntu if i can get the sound in jaunty to work, but im too much of a newb to fix it.  i tried editing /etc/modprobe.d/alsa-base.conf, but no luck.

but i digress.

assume i ran jaunty x64 as the host, gave it 2gb of swap space, and gave the guest win7 x86 3gb ram, and gave each os half of my video memory, would that run well?

i'd like to use ubuntu, but without native support for the adobe master collection (neither cs3 or cs4 work) i need to virtualize.

---

### Post by lykwydchykyn on 2009-07-01
You are probably better off not setting up a situation where anything is going to use swap.  Since all these settings are changeable, you can probably just start out with some conservative settings and bump it up as needed.  I've found there is a point of diminishing returns with allocating resources to guest OS's; you end up starving the host OS to a point where both OS's run terribly.

---

### Post by np0731 on 2009-07-01
sorry if this is a dumb question, but is there any way to run the cs4 product suite without virtualizing windows?

if a virtual machine will mean degraded performance, it sounds less and less like a valuable way for me to work.

---

### Post by Idefix82 on 2009-07-01
> **np0731 said:**
> sorry if this is a dumb question, but is there any way to run the cs4 product suite without virtualizing windows?

I'm afraid the answer is no. CS2 seems to be decently supported by Wine now, but CS4 not yet. Why don't you opt for a dual boot setup?

---

### Post by lykwydchykyn on 2009-07-01
> **np0731 said:**
> sorry if this is a dumb question, but is there any way to run the cs4 product suite without virtualizing windows?

if a virtual machine will mean degraded performance, it sounds less and less like a valuable way for me to work.

"Degraded performance" is relative.  I run a virtual winXP on my work machine (Dell Opti 745 w/4GB of RAM) and hardly notice when it's on.  Obviously you cannot run two operating systems at the same time and expect each to perform as if it had the entire machine to itself; the question is whether or not the lost resources were something your app would have used in the first place.

I would imagine CS4 can use some resources, though I don't do graphic design myself.  In any case, you lose nothing but time to try it, and if it doesn't work out you can dual-boot.

---

