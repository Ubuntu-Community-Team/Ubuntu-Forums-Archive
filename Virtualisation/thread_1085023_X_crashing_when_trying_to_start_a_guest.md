---
title: "X crashing when trying to start a guest"
date: 2009-03-02
forum: Virtualisation
---

### Post by Xkutzy on 2009-03-02
I have a Dell Optiplex gx620 which has a Intel GMA950 on board. I have been trying to set up virtualization on it without success. Every time I try to start the Win2K guest OS my X session crashes.

Originally I had Hardy installed. I tried VMware server 1.06 as per the sticky. That crashed X when I tried to start the guest. So I tried VirtualBox as per that sticky. That crashed X as well. This machine is dual boot so I installed VMware sever in XP on this machine. That works fine. I upgraded this PC to Intrepid and installed VMware 1.07 as per that sticky. Again X crashed but this time I got an error message.

(EE) intel (0): No valid modes
(EE) Screens found, but none have a usable configuration.

X then re-starts in a "low graphics" mode that does not look much different. In this mode, VMware works!

So it looks like this is a video driver issue. With the Intel driver loaded VMware will not start a guest. I assume that "low graphics" means the VESA driver is loaded and this works.

I have tried upgrading the intel driver from 2.4 in Intrepid to 2.5 from testing but that hasn't fixed the problem.

Has anyone else experienced a similar problem? Can anyone think of anything else I could try? My only thought is to buy a cheap Nvidia card and try that, but I am loathed to do this as the PC runs a bit too hot for my liking as it is.

---

### Post by Ng Oon-Ee on 2009-03-04
I'm not sure exactly why virtual machines would crash your X, this sounds (as you have mentioned) like an Intel problem. Would suggest bringing it to the appropriate place, doubt any here have the expertise. Can either try the hardware and laptops subform or linuxforums.org, which I have found to be slightly more technically oriented than here.

---

