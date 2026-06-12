---
title: "Switched from VMWare Workstation to VirtualBox"
date: 2011-01-10
forum: Virtualisation
---

### Post by HDave on 2011-01-10
Ever since VMWare workstation 6.5, I have noticed that VMWare has been making my 32 bit Ubuntu hosts periodically hang for a few seconds.  I have also noticed the virtual machines getting more and more laggy. 

After repeated failed attempts over the past 12-18 months to fix it I finally decided to try VirtualBox.

Wow -- I feel like a complete idiot for not having made the switch before.  VB is faster, the virtual drives are smaller, and the thing has no lag, hang-ups, etc.  It Just Works.

I thought I'd post this to help push any other folks suffering under VMWare Desktop products to give Virtualbox a try.  You will not be going back....

Of course all this means that I'll have to take a closer look at KVM for the server-side virtualization next time we rebuild our server.....

---

### Post by CharlesA on 2011-01-10
I've heard that KVM is pretty good, but I haven't really messed with it. I mostly use VirtualBox for anything I need to virtualize.

What version of Virtualbox are you using, by chance?

---

### Post by HDave on 2011-01-11
v4.0 -- Brand spanking new release.  Added their repo to my Lucid sources and install was a snap.

I am running 30+ servers on VMWare Server right now.  Heard good things about ESXi and was planning to upgrade to that.  But the whole VMWare Workstation just soured me so bad, I'm going to try KVM.  Plus I like the idea of having my own private cloud on the cheap via Eucalyptus.

---

### Post by CharlesA on 2011-01-11
Nice. I have VBox 4 installed on a test machine atm, as I am testing it to make sure the new release of phpvirtualbox works well (and it does for the most part).

I'll probably stick with 3.2 for the time being tho.

Also: I use ESXi at work and it works great for a baremetal hypervisor.

---

### Post by Santos1204 on 2011-01-11
Just ported my machine over to ubuntu 10.10 but since I'm working in a windows environment I need to have a good/solid/fast VM to use for most of the day under Win7, tried KVM and found that the viewer (VNC?) is slow looks a little like odd and doesn't full screen well, so tried virtualbox (and despite my reservations about oracle) it's a very good solution. Make sure you download the full version rather then the OSE version for USB support.

---

