---
title: "Windows 7 screen resolutions"
date: 2012-11-10
forum: Virtualisation
---

### Post by Anaxagore on 2012-11-10
Hi,

I have been running Windows 7 within VirtualBox (latest proprietary version) in Ubuntu 12.10. I want to be able to use the full resolution of my laptop (1920x1080) in full screen mode, but screen resolutions that are proposed to me jump from a 1440x1050 to 1600x1200 and 1920x1200.

I did run the VBoxManage setextradata command to add the "CustomVideoMode1" that I set up at 1920x1080x32, and the enumerate command of VBoxManage does list 1920x1080x32 in the properties of my Windows 7 virtual machine, but Windows 7 still (even after restarting Ubuntu) does not propose me the 1920x1080 mode.

It is the first time I actually use my laptop as a real laptop and move it away from its docking station that is connected to an additional monitor. This monitor has a 1920x1200 resolution, so I never noticed the issue earlier (that virtual machine has been set up one year ago), and I am not even sure that the 1920x1080 resolution does not appear in the list that Windows 7 proposes me when the virtualbox is started with the external monitor connected..

Anyone has an idea on how to fix this issue?

Thanks in advance!

A.

---

