---
title: "Mouse issues in Sun VirtualBox with dual screen"
date: 2010-02-02
forum: Virtualisation
---

### Post by caradeporra on 2010-02-02
I have Ubuntu 9.10 Karmic Koala. I have a dual screen setup using NVIDIA drivers (which is MUCH improved over the previous versions of Ubuntu - good job guys!). I am running a virtual XP through the Sun VirtualBox, the full version.

The problem I am having is while in the VirtualBox, the mouse and keyboard do lock into the virtual machine. However, the mouse will 'skip out' -if you will- of the virtual machine and just mess it up. I put the 'eyes' at the top bar that follow the mouse so I could see what is happening.

It appears that if you go too far right, the mouse will move to the second screen even though it should be locked in the VirtualBox. Also, if you move it too far left it does the same thing!  When it does this the moust gets lost because it exits the Virtual Machine, but it is not in Linux either.  This is very annoying, because every it always interrupts. You have to 'find' the mouse again and re-center it so it doesnt immediately do it again.

Is anyone else having an issue like this, and any advice?!?

I tried to be as thorough as possible with the details, but let me know if there is anything else you need to know, or if you are confused about the setup.


Quote:
Originally Posted by howefield View Post
If you have guest additions installed, this is correct behaviour. The mouse will travel between host and guest operating systems without having to be released from the guest.

Are you saying that you want the mouse to be captured within the virtual machine and to use a keyboard shortcut to free it to your host.

Or have I misunderstood ?
The mouse is already captured within the virtual machine, however if you travel so far that the mouse, while captured, travels to the other monitor in Linux, then the mouse stops responding in the virtual machine. And because it is captured in the virtual machine, the mouse is "Lost" on the second monitor unable to due anything...

Monitor 0 has VirtualBox VirtualBox is on 1 monitor ONLY (there is not dual monitor set up in VirtualBox. Monitor 1 is simply the second desktop in Linux. But while the mouse is captured in the virtual machine, it will still skip to Monitor 1.

Does that help? Kinda confusing, I know.

---

### Post by caradeporra on 2010-02-03
gave up and enabled the guest setting so that mouse would just integrate.

---

