---
title: "VirtualBox runs 11.04 far slower than VMware"
date: 2011-08-11
forum: Virtualisation
---

### Post by Stormblazer on 2011-08-11
I've always used VMware in the past, and decided to give Virtual Box a try. I loved the support for OpenGL and the significantly better configuration options in Virtual Box, but the speed difference is enormous.

Both VMs are allocated 1GB of RAM, allowed to use all four CPU cores, and are stored on an SSD. The host is Windows 7 64-bit while both guests are Ubuntu 11.04 64-bit, the host has 4GB of RAM (but I ran the VMs independently of each other) and a 2.8Ghz Intel Core2 Quad. Both VMware Player and Virtual Box are the latest versions available at the time of this posting.

Virtual Box takes around 3 times longer to do anything compared with VMware - where VMware boots and loads almost as fast as Windows itself (which is very fast on an SSD), Virtual Box is painfully slow, taking nearly a minute to even boot, and another minute to login. Launching programs has a significant delay, and the overall responsiveness is much lower than VMware.

Is there some setting I'm missing here, or what? I want to use Virtual Box, but at the moment it seems unacceptably slow.

---

### Post by Jake.Debord on 2011-08-11
> **Stormblazer said:**
> I've always used VMware in the past, and decided to give Virtual Box a try. I loved the support for OpenGL and the significantly better configuration options in Virtual Box, but the speed difference is enormous.

Both VMs are allocated 1GB of RAM, allowed to use all four CPU cores, and are stored on an SSD. The host is Windows 7 64-bit while both guests are Ubuntu 11.04 64-bit, the host has 4GB of RAM (but I ran the VMs independently of each other) and a 2.8Ghz Intel Core2 Quad. Both VMware Player and Virtual Box are the latest versions available at the time of this posting.

Virtual Box takes around 3 times longer to do anything compared with VMware - where VMware boots and loads almost as fast as Windows itself (which is very fast on an SSD), Virtual Box is painfully slow, taking nearly a minute to even boot, and another minute to login. Launching programs has a significant delay, and the overall responsiveness is much lower than VMware.

Is there some setting I'm missing here, or what? I want to use Virtual Box, but at the moment it seems unacceptably slow.


I don't think I would give up on vbox too quickly... I'm not that sure about why exactly your speeds are slower, but I will say this... My winxp VM's boot pretty fast with only one core and the same 1gig ram you have specified. I'm just going to throw something out there and suggest checking to make sure the VM is using all 4 cores.

EDIT: BTW, my host machine is headless Ubuntu. I just rebooted my vm to test boot speed. It took 5 seconds... and a full reboot only took 12. Given this is a fairly fresh install not much loads after boot. Just thought I would throw out some numbers

---

### Post by Stormblazer on 2011-08-11
Alright, I checked and all four cores seem to be used and seen according to the resource monitor and /proc/cpuinfo.

I tried switching the chipset to PIIX instead of ICH9, and bootup is comparable to VMware now. Login time however is still incredibly high (over a minute, sometimes two), but since entering/restoring from saved state is actually faster than VMware that's not a huge issue. I also tried disabling 3D acceleration, which had no effect.

Unfortunately, run time speed remains a problem. Delays in responsiveness can be measured in seconds for doing nearly all tasks, even just switching between tabs in a web browser, and CPU usage is very high. Are there any settings I can fiddle with outside of the GUI, or known conflicts with certain settings I should be aware of?

---

### Post by Jake.Debord on 2011-08-11
What do you have the video ram set to?

Also, what version of vbox are you using?

---

### Post by Stormblazer on 2011-08-12
> **Jake.Debord said:**
> What do you have the video ram set to?

Also, what version of vbox are you using?

Video RAM was initially set to default, raised it to 64MB, then lowered to 32MB. No noticeable difference running at 1680x1050.

Version is the latest off the website, 4.1.

---

### Post by Derek Karpinski on 2011-08-15
Try turning OFF 'APCI'......of course you can only give it one core then, but it made a world of difference for me.
 
Give it the max amount of video RAM (128MB), and 1-1.5GB of RAM.

---

### Post by Jake.Debord on 2011-08-15
> **Derek Karpinski said:**
> Try turning OFF 'APCI'......of course you can only give it one core then, but it made a world of difference for me.
 
Give it the max amount of video RAM (128MB), and 1-1.5GB of RAM.


128 may possibly be the max for you, but that's not universal... I have mine set to 256mb


I agree with turning off APCI at least for the moment. You can tweek it later if you feel like it.
ALSO, and maybe more importantly:
At a resolution that high depending on your color depth you may want to google what the recommended vram for that kind of resolution is. Also, depending on what you have running I would recommend at least 1gig ram.

---

