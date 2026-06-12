---
title: "VirtualBox is running extremly slow when in WOW"
date: 2012-03-11
forum: Virtualisation
---

### Post by lanzd on 2012-03-11
I'm not a 100% sure what information one would need to effectively help me, but I'll supply what I can.  If there is anything else you need just let me know.  I'm running Ubuntu 10.04 as my host OS and windows xp x86 as my guest.  I installed virtualbox 4.1.8 from virtualbox.org and installed the guest additions 4.1.8r75467 while in safemode.

When I'm on the desktop and browsing the web it's not as fluid as I would like but nothing that seems too extreme as far as speed.  However, when I enter World of Warcraft my FPS is extremely low, but the latency is also low.  Average latency is ~90:home, and ~120: world.  Yet I'm getting 1fps half the time and 0 the other half according to the Wow UI.  My download speeds outside of wow are pretty consistent with what I get on my host.  ~1-1.5 mbps.  It just seems extremely odd for there to be such a discrepancy between the latency and fps.

As far as my setup, I have an MSI 890FXA-gd65 motherboard, amd x1100 6core processor, MSI N560GTX TI twin frozr II GPU, 16gb of ddr3 2000 ram and a 5600rpm 1tb barracuda HDD.  I have set aside 3 cores for the VM and 3584mb of ram.  I have IO APIC enabled,   and 3D Acceleration and 2d video acceleration enabled.  

Again, If I am missing any information just ask.  Thank you in advanced for your help.

---

### Post by synaptix on 2012-03-11
Virtualbox is simply made to test OS and run simple 2D applications, as 3D support still isn't on par as native 3D. I'd guesstimate a virtualbox to be capable of around 90% of native performance. 3D applications are just out of the question on vbox.

You'd be better off running WoW in Wine if that is your sole intention.

---

### Post by lanzd on 2012-03-11
Ohh, all right.  Thank you for you quick reply.  And yeah, that is my sole intention, WoW and other games.  I've been running them via wine but thought I would get better results in a VM.  Is there another VM software that is capable of this?  or does this apply to all VM software at the moment?

I'm assuming when you said "You'd be better off running WoW in Wine if that is your sole intention. 	", you were including other vm software and not just Virtualbox but I just want to make sure.

Thanks

---

