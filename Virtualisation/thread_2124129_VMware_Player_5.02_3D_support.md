---
title: "VMware Player 5.02 3D support"
date: 2013-03-09
forum: Virtualisation
---

### Post by Slimmons on 2013-03-09
Hi, I'm running Ubuntu 12.04, and I have VMware player 5.02.  I am trying to run a windows 7 VM in order to player warcraft III.  I always get the message at the start "Hardware graphics acceleration is not available", but In the display options I have Accelerate 3d graphics checked.  I have installed opengl (or at least followed instructions on a site).  Anybody have any advice?  I'd be happy playing wc3 on wine, but I get some delay, and have had a few other problems, so if someone knows how to fix the delay I have on wine, that would also be a good answer.  Thanks

---

### Post by meteorrock on 2013-03-11
Might want to upgrade your VMware hypervisor to the latest builds. I am using VMware workstation 9.0.1 and acceleration works fine. The "workstation" for Vmware are for end users and workstations like a tower or laptop, and that series of builds from Vmware gets more attention than just the standard player. You can download and use that hypervisor for free if you look on the internet some. Do you have your BIOS set up for virtualization for AMD-v/rvt or VT-x? Unless you have went into the settings of your Windows 7 host for virtualization, depending if your processor will handle it, you will have problems with the settings in VMware. Any processor or computer less than 4 years old should support virtualization in the BIOS of the computer.

Also do you have the vmware tools installed inside of the hypervisor? Without vmware tools set up properly you will also run into problems with settings with your hypervisor if you are running Ubuntu as a Guest OS. So check the settings on your Vmware hypervisor to see if vmware tools are installed.

---

### Post by Helios747 on 2013-03-12
VMWare automatically and silently disables 3D acceleration if you're using Intel graphics or some AMD cards because it doesn't work properly on those. If this is the case, there is nothing you can do.

---

