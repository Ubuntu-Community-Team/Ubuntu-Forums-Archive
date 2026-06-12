---
title: "[SOLVED] Which is better?+ Do they use my videocard?"
date: 2008-02-26
forum: Virtualisation
---

### Post by emshains on 2008-02-26
I am a noob in virtual desktops, so here it goes:
I tried to use VirtualBox  to emulate windows XP, but since i didnt really have any time today i didnt install it. 
But then the question rose (like the rise past form): Which is the best Virtual desktop emulator to run on 1,6ghz sempron with 768mb ram and a nvidia 7300gt?

And do these emulators use my actual video card or they just use ram?
and do they use all of actual ram or they only use swap?

Ive tried to google it, but with no real results.


Already apologizing for my bad english and waste of your time....

---

### Post by luisromangz on 2008-02-26
A sempron probably is a weak machine for an intensive use of virtual machines, but you can try and see yourself.

VirtualBox is a great virtualization program for casual desktop use, on par with VMWare, at least with the free version of it.


Virtualization software doesn't virtualize the host's system graphics card, because it is a single device which is not designed to be shared between two operative systems. Instead, the virtual machine software offers the guest system a driver that enables it to better interact with the host machine and somewhat accelerate the drawing, but virtual machines aren't designed for gaming ;)

It will use real RAM, and will swap if you asign the virtual machine more ram than it's actually avalaible in your system because other proceses and stuff.

---

### Post by emshains on 2008-02-26
So its ok to use Virtual Box for some desktop emulation?

I am not going to do it like frequently, just to test some cool operating systems or things like that.

Thanks for the response!

---

