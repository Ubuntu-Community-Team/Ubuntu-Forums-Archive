---
title: "Should I run Ubuntu on top of Vista?"
date: 2008-10-21
forum: Virtualisation
---

### Post by fongandrew on 2008-10-21
A bit of a noob on virtualization, so apologies in advance for anything stupid I say.

I want to run Vista and Ubuntu side-by-side without dual-booting I could care less about security and performance, at least for now. I'm thinking of virtualizing Ubuntu on top of Vista. Here's why:

1. I recently ordered a Lenovo T400, and since it's relatively new hardware, there appear to be a few driver issues. I really don't want to deal with those at the moment, so if I run Ubuntu inside a VM in Vista, hopefully I can avoid some driver issues.

2. My previous laptop's installation of Ubuntu had less than stellar battery life. A lot of the power savings from the T400 seems to come from Lenovo's power management software. If I run Ubuntu inside a VM (and little else), perhaps I could get a little extra battery life than if I ran Ubuntu straight.

Do these reasons make sense? Or do I have this completely backwards? Thanks!

---

### Post by jpkotta on 2008-10-21
Given what you describe, the drivers reason seems reasonable to me.  And maybe that's enough to decide that this is the way to go.

I doubt that you will get better battery life running a VM.  Ubuntu will still do the things that make your battery die faster, with Windows doing other things that make you battery die faster on top of that.  

Ubuntu can be tweaked to be very power efficient.  It takes work and know-how.  Try lesswatts.org.  After dealing with both Ubuntu and Windows and trying to get all the stupid background stuff to stop, I have to say it was much easier in Linux, albeit not as "simple".  The difference is, as you point out, OEMs will tweak Windows for you.

---

### Post by lkness on 2008-10-21
I am running Ubuntu in VMware's free Server software, and it works well. My main problem is that i can't get Vista to recognize the virtual machine. So i can't ftp or ssh between the two machines. I end up emailing things between the servers. I'm not a network guy, so it could be setup, but i spent several days trying to get it to work. You may have better luck. I think the problem is in Vista's new security. 

If you have VMware's workstation, it might work better. 

As for Ubuntu in the VM, it works well. I don't have the mouse wheel working, and VMware server doesn't support bridged network access on wireless cards. Must use NAT.

Virtual PC on Vista running Ubuntu doesn't work. 

If using VMware, make sure you install the VMware tools. 

Lanny

---

