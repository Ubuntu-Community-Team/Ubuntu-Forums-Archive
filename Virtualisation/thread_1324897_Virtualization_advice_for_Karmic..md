---
title: "Virtualization advice for Karmic."
date: 2009-11-12
forum: Virtualisation
---

### Post by 1clue on 2009-11-12
Hi,

I have been using various VMware products for years.  I use several images for software development and testing purposes, including a Windows image for SQL Server.

I upgraded to 9.10 without checking VMware issues, for some unknown reason.

I have no issues with VMware, EXCEPT that it breaks more often than any other piece of software I have ever known.  Every kernel upgrade, you have to monkey with it to get your VMs working again.

I'm considering changing to something else.  It appears to me that Xen is the thing I want, but I'm not sure.  I'm on a workstation, but it's an i7 and has plenty of RAM for what I need, I built it specifically for virtualization.

My requirements are as follows:
[LIST=1]
[*]Need 64-bit and 32-bit simultaneously on different VMs.
[*]Low maintenance for administration.
[*]Needs to support Windows 2003, XP and 7 as well as Linux variants with at least 2 images running simultaneously.
[*]It would be really neat if I could continue to use my VMware files.
[*]I'm a software developer, not a virtualization jockey.  This needs to not be somebody's full-time job.
[/LIST]

What I'm after is a comparison by someone who has used the virtualization server in a similar situation, and can tell me how much of a PITA it is compared to VMware, and whether any of the workable solutions tolerates normal software updates better than VMware.

It would also be helpful to know an ETA on a stable VMware Server for Karmic/64.

---

### Post by fjgaude on 2009-11-13
From what I can see it is better to stick with what works and only do security updates. No kernel updates, for all the virts require kernel re-compilies as they come out. I've lived with this situation since 6.04 and vmware server 1.0.6.

Now with 9.10 there is nothing I know of that works except with actual kernel patches and re-compilies. Server 1.0.10 works with 9.04, 8.10, 8.04.

Player 3.0 works with 9.10 but doesn't permit remote access of VMs. So that is out for WAN or LAN.

I've not seen any schedule for fixes, either from VMware or Ubuntu. Workstation 7.0 may be a solution, but it costs $99.00. <sigh>

---

### Post by 1clue on 2009-11-13
Karmic fixed a whole lot of other things I was waiting for, but somehow I didn't pay attention to VMware.  All the older builds, including 9.0.4, are missing things that I consider to be important if not critical.

Then there's the problem of the licenses for the VMware Windows guests, those are real licenses owned by my company.  I'd have to be able to convert those images over to Xen or whatever I switched to.  I'm sure the processor type etc will change if I do that, and all the drivers.  I'm not sure if we have extra license keys for that, or if the key would be transferable.  Surely the OS would detect that and complain if not completely refuse to work.

Paying a small fee for commercial software doesn't bother me, even if it were my money.  In this case, it would be expensed to my company and would belong to my company, same as the images on VMware.  $99 is a small price to pay, if it actually works and is reliable.  I spent way more than that of my time with this upgrade, trying to get it to work.  But I don't think it'll really change anything that way.  For that matter, the software cost of the OS and software on these images is large compared to that, even considering that much of it is developer license.

I need to be able to test our software against real installations of operating systems our customers use.  Getting a separate physical computer for each of those operating systems is ludicrous if it can be done any other way.  These installations need to stay valid and current in upgrades, because our customers do the same.

The more I think about it, the more I think I have to stick with VMware for the existing images.  This weekend I guess I'll have to sit down and figure out how to get VMware working on Karmic.

I'd still like to figure out Xen, it seems like it might be less problematic for future installs.

Thanks.

---

### Post by fjgaude on 2009-11-13
Well, I've moved vmware server-created VMs to other CPUs, motherboards, boxes without much issue. In the case of moving Windows you have to make a Hardware Profit under System Properies in the present hardware, move to the next with the whole VM folder copied over, and when you play the VM, Windows will note you have new hardware, answer the questions and you are good to go.

I believe that if you google the issue or if you study the Sticky at the top of this forum you wil get enough info on how to proceed with certainty.

Good luck!

---

### Post by 1clue on 2009-11-13
I've already upgraded VMware several times, that's not what I was saying.  I was thinking of migrating from VMware to Xen.  I'm not sure that would work at all.

Or are you saying that it WOULD work, even changing virtualization technology?

---

### Post by fjgaude on 2009-11-13
I can't say anything about Xen, but from what I've read here I'm not sure the free versions are that full featured. Maybe bodhi.zazen, one of the moderators, will report in. Or place a post into the Sticky and ask.

---

### Post by fjm03 on 2009-11-13
*I've not seen any schedule for fixes, either from VMware or Ubuntu*

My guess is that neither Concanical nor VMware will make the effort. But someone, probably within the VMware community, will solve the problem and then someone, wiithin the Ubuntu community,  will translate to fix into script and terminal commands that the average, Ubuntu desktop user can employ.

As an example, I would probably have 2.0.2 up and running on 9.10 if I knew what command to use to "*evoke*" or how to command a patch to "*run*".

---

### Post by stubrownuk on 2009-11-17
I tried running VMware in Karmic, absolutely useless. I have not tried VirtualBox with Karmic, so that may work, but you can't port a VMware VM to VirtualBox as far as I know (which makes sense because they each use their specific ways of storing VM info). So I have now gone back to running Jaunty on all three of my business machines, because that works with full virtualisation support. I guess when it comes to upgrading to Karmic, the good old saying applies with a vengeance: "If it ain't broke, don't fix it."

I'd like to say that I'm impressed with Karmic, but too many things don't work at the moment for my liking, especially virtualisation.

---

### Post by antiram on 2009-11-17
my xp installation was installed with vmware-1, ported to vmware-2 and then ported to kvm and it works.

maybe if the vmdk image has more parts because snapshots or so the vmdk parts must concatenated with a vmware tool before. And uninstall the vmware-tools in windows before porting, they cannot removed without  underlying vmware virtualisation.

---

