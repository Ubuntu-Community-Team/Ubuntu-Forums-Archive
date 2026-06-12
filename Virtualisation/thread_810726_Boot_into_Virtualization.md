---
title: "Boot into Virtualization?"
date: 2008-05-28
forum: Virtualisation
---

### Post by Hardrive on 2008-05-28
I don't know why this is possible, but I would really like to be able to do this.  Currently, I have my system setup in a dual-boot configuration, with Windows and Ubuntu.  While I'm in Ubuntu, I would like to virtualize that Windows installation, so that I can use all of the programs that I have installed.  However, I would like to be able to restart my computer, and boot right into that Windows installation from Grub. 
 

Does this make sense, and is it possible?

---

### Post by burgechris on 2008-05-28
I'll tag along in here as my question is similar.  Below is my post from the beginner forum.  I don't need to keep the dual boot option in the end.

Original Post:
I have, not a unique question, but more of a "can it be done and how" question. I'm coming from an XP SP2 machine that I now dual boot with Ubuntu 64 bit (for AMD). I want to take the existing setup in XP and put it into a virtual box. This is mainly for development in existing projects that I do using Visual Studio 2005. Unfortunately, it is going to take months before I am able to get my Visual Studio DVDs out of storage but now is a great time to switch over to linux. The XP configuration is what I need until I'm done with these projects and I have my full setup completed on Ubuntu.

Thanks,
Chris

---

### Post by LeoSolaris on 2008-05-28
From what I have learned so far about virtualization, it doesn't seem like you can virtualize an existing install from a separate partition. The virtual version is a completely fresh install. The hardware virtualized for this install is not actually the same hardware your computer is made of, so a direct transfer is not possible with Windows because it really gets grumpy with sudden changes in certain hardware.

A work around that may interest you would be to pick up a second computer, just without the monitor, keyboard, or mouse. You can attach it and your existing computer to a device called a KVM Switch (Radio Shack) They will both be piped into your monitor and with a flip of the switch you can hop over to the windows computer, then flip it back and your in the Ubuntu computer.

I am not an expert on virtualization, but so far I have not seen a way to do what your talking about. Virtualization is still in it's infancy, sort of like the way the internet was back in the late 80's and early 90's. It will get more sophisticated as time goes on, and most likely include what your talking about doing.

Leo

---

### Post by Hardrive on 2008-05-28
I didn't think that it was possible, but I was just curious, as that would be very cool.

Windows would freak out about the constant changes in hardware and probably invalidate itself too.

---

### Post by LeoSolaris on 2008-05-28
> **Hardrive said:**
> I didn't think that it was possible, but I was just curious, as that would be very cool.

Windows would freak out about the constant changes in hardware and probably invalidate itself too.

Yep, we all know how touchy and fragile those little windows are. We simply keep them around for the entertainment value.

---

### Post by bradmkjr on 2008-05-29
You have some valid points, and I would like to expand on them. The hardware issue is big, and booting between back into Windows may cause problems. If you are lucky enough to have a corporate licensed version then it may not notice the change in hardware. XP home or Vista is hte most sensitive. 

as far as the KVM, that is old school, it works but it is faster, easier, and less clutter to use Remote Desktop or VNC. If you where go go thise route, it would allow your current computer, via remote desktop if you choose, to be accessed from any where in your home network, of it you wantd to anywhere in the world, if you have a static IP. much better then sharing KVM setup. you can use ubuntu as you web browsing, e-mail, typing, and then remote desktop into windows for visual studio. 

With VMware or Virtual Box you could possibly use the current install of Windows partition inside of a VM, but not if it is on the same partition as Ubuntu.

Good Luck,
Bradford Knowlton
[http://x86Virtualization.com/](http://x86Virtualization.com/)

---

