---
title: "VirtualBox (size of host partition?)"
date: 2008-07-17
forum: Virtualisation
---

### Post by SeePU on 2008-07-17
Can someone tell me what size the partition should be if K/Ubuntu is the host of a VirtualBox setup?

Also, if I am dual booting, I might have partitions set up of 15-20GB per distro.  I just want to have some distros installed for dual boot and then I will compare to VirtualBox setup.  When I install a distro in the VirtualBox (in Ubuntu host), will I set up and partition the same?

I am trying to find discussions on this but not having much luck.   I searched the forum and also googled.  I usually only install the one partition and my / (root), /boot and /home is in the same partition.   I usually use another hard drive for my data.  What do you think?

I am still experimenting so I haven't seen the need for a separate home or boot partition yet.  I just think it will be too hard to keep track of so many partitions especially if I will have many for dual boot.   If I use VirtualBox, how do you recommend setting this up and how would you install multiple OS's in it?   I thought K/Ubuntu would be a good distro as a host since there is probably a lot of discussion about it and decent support.  

Thanks for reading and for any advice.   Cheers.

---

### Post by HotShotDJ on 2008-07-17
> **SeePU said:**
> Can someone tell me what size the partition should be if K/Ubuntu is the host of a VirtualBox setup?I'll be honest with you, I'm not sure I understand what you are asking in your post... but I'll give it a go.  The size of each virtual disk depends on what you plan on doing with the virtualized OS.  15-20 Gig per VM sounds reasonable.  Now, add up the number of OS's you wish to have installed and there is your minimum size of the host partition.

You mention that you use only one large partition for your Linux setup.  Thats not a very good idea, although it IS the default set up for most installers.  At minimum (for a home set up) you should have a separate /home partition.  I have found that 15 gig for the root partition plus a 1.5 X RAM (2 X RAM if RAM <= 1024 MB) Swap partition is sufficient with the remainder of the drive as /home.  NOTE:  This will not work if you make extensive use of /var.  If you don't know what I mean by that, then you don't need to worry about it.

As far as I know, you could set up your virtual machines to run from an external harddrive.  You'd take a performance hit, of course, but only you can decide if that hit would be tolerable.

You can have as many VM's as you wish.  The only limit is the size of your hard drive.  However, you generally can only run them one at a time.  REMEMBER: The RAM assigned to the VM is NOT available to the host OS while the VM is running.  Be sure to take this fact into account when adjusting the VM RAM settings!

All my machines run Ubuntu as the main OS.  One has a Windows 2000 guest VM and the other has a Vista Home Premium guest VM.  Is Ubuntu the "best" for running VirtualBox?  I don't know.  I DO know it works well for me.  Feel free to refer to the [VirtualBox end-user documentation page]("http://www.virtualbox.org/wiki/End-user_documentation").  I've found it very useful.

---

### Post by SeePU on 2008-07-17
> **HotShotDJ said:**
> I'll be honest with you, I'm not sure I understand what you are asking in your post... but I'll give it a go.  The size of each virtual disk depends on what you plan on doing with the virtualized OS.  15-20 Gig per VM sounds reasonable.  Now, add up the number of OS's you wish to have installed and there is your minimum size of the host partition.
So, if I use Ubuntu as the host, if I want the following OS's as guests:
*Ubuntu
Sidux
Debian Lenny
Mepis
Fedora
Mandriva
OpenSUSE

Then the Ubuntu host OS needs to be 120GB?   So, I would need the Ubuntu 8.04 partition to be 120GB when I install so that when I install VB, everything is prepared for that?  If I am wrong there, then you have ultimately confused me or I am not grasping things yet.

> You mention that you use only one large partition for your Linux setup.  Thats not a very good idea, although it IS the default set up for most installers.  At minimum (for a home set up) you should have a separate /home partition.  I have found that 15 gig for the root partition plus a 1.5 X RAM (2 X RAM if RAM <= 1024 MB) Swap partition is sufficient with the remainder of the drive as /home.  NOTE:  This will not work if you make extensive use of /var.  If you don't know what I mean by that, then you don't need to worry about it.
You can share swap partitions but I thought it was a big 'no-no' to share home partitions.  If you are someone who experiments and has an expansive multi-boot system, that would mean a lot of partitions if you have a separate home for each OS plus the root per OS.  Or am I confused?  Your method works perfectly if you only have 1 or two distros installed.  I guess the VB works for that kind of setup.  However, I was going to have 6 or 7 distros installed so what would the best path/method to take, then?

I just want to use the grub/multi-boot method until I am experienced enough to deal with the Virtualization/VirtualBox issues that will inevitably come up especially when I'm unfamiliar with both the program and concepts.  People who are adept at using Linux still have problems/issues using VirtualBox as I've read from various respective distro's forums and VirtualBox forum itself.  

> You can have as many VM's as you wish.  The only limit is the size of your hard drive.  However, you generally can only run them one at a time.  REMEMBER: The RAM assigned to the VM is NOT available to the host OS while the VM is running.  Be sure to take this fact into account when adjusting the VM RAM settings!
I've been told that and read it!  Thanks for the confirmation.  I have 2GB in my machine right now.  Would I benefit to add another 2GB or is 2G enough?  How much RAM should I assign per distro?  Since I can only have one VM, I might as well give it a decent chunk of RAM, right?  Like almost 1GB?  If I had 4GB in the machine, would that cause problems for the 32-bit OS's like Windows and a Linux OS in a normal multi-boot arrangement?  I've never had a machine with 4GB of RAM and haven't read up on what happens when you do have that much RAM.  I just know that 32-bit OS's (probably?) can't use all of it.  

> All my machines run Ubuntu as the main OS.  One has a Windows 2000 guest VM and the other has a Vista Home Premium guest VM.  Is Ubuntu the "best" for running VirtualBox?  I don't know.  I DO know it works well for me.  
It does sound like a good idea.  I could run the VirtualBox with 6 or 7 VMs (guests) and then have only two or three traditional OS's in a multi-boot.  But, that would allow for less partitions in the traditional way and I could have the extra partitions of /home and root.  I know about the swap needing 1.5x the RAM.  When you install the guest/VM, would you divide the partitions up with separate home and root?  You sound like you only have Window VMs and no Linux guests yet?

---

### Post by snowpine on 2008-07-17
Hi SeePU, your posts are still a little confusing... Are you talking about one Virtual Machine with 7 different OS's, or 7 different Virtual Machines, each with 1 OS? 

I guess it all depends on your goals and what you are hoping to achieve. If you are just looking to try out a bunch of different distros, I would recommend a separate VM for each. You'd have your Fedora VM, your Debian VM, and so forth. Give each one a 10-20gb virtual "hard drive" and however much RAM it requires. 

If you put all the OS's into one VM, you can only use one at a time, but if you have them separate, you can have two (or more, if you have enough RAM) running at a time and compare them.

It's all about what you're trying to accomplish, which is not clear from your question.

---

### Post by SeePU on 2008-07-17
Okay, I guess I was thinking about the first way, one VM.

But, yes, I would be using VirtualBox (for e.g.) for trying out distros so it sounds like the 2nd way is better.   So, I would have a separate VM for each then?   

But, I still don't know how it works.  If I am doing this in Ubuntu, how large does the Ubuntu partition have to be?  I don't want the Ubuntu OS taking up the entire drive as I would still multi-boot the traditional way.   

For e.g., if I have five separate VMs and using Ubuntu as the host OS, how does the drive look like?

---

### Post by snowpine on 2008-07-17
> **SeePU said:**
> You can share swap partitions but I thought it was a big 'no-no' to share home partitions.  If you are someone who experiments and has an expansive multi-boot system, that would mean a lot of partitions if you have a separate home for each OS plus the root per OS.  

I believe it is safe to share a /home partition among different distros IF you use a separate username for each distro (that way there is no overlap)

---

### Post by snowpine on 2008-07-17
> **SeePU said:**
> 
But, I still don't know how it works.  If I am doing this in Ubuntu, how large does the Ubuntu partition have to be?  I don't want the Ubuntu OS taking up the entire drive as I would still multi-boot the traditional way.   

For e.g., if I have five separate VMs and using Ubuntu as the host OS, how does the drive look like?

Your host would probably look like this (assume a 100gig hard drive for the sake of argument:

98gig Ubuntu partition
2 gig swap

or

10gig Ubuntu partition (maybe 20 gig if you have the space)
88gig /home partition
2 gig swap

It is not necessary to create a partition for each virtual machine... that's what "virtual" means! :) The "hard drive" for each VM is just a big file in your /home partition.

---

### Post by Shazaam on 2008-07-17
You also have the option of creating either a "dynamic" (vm automatically increases in size) or "static" (vm size never changes) virtual machine type. If you have a small (or have a lack of space) host hard drive(s) I would stick with a "static" virtual machine. If you click on "Help" in the main VirtualBox window it will explain the differences.
The only time I had any problem with a dynamic virtual machine get out of hand size wise was when I had what I called a "Massive Multi-Boot" vm. I had  a virtual machine with two virtual drives which had 8 operating systems installed on them. I only had an 80 gig host drive at the time which had WinXP (35 gigs in size) and the multi-boot vm grew to 32 gigs.
Normally my dynamic vm's range in actual physical size from 2 gigs to about 7.5 gigs and thats with all of them updated.

---

### Post by HotShotDJ on 2008-07-17
> **SeePU said:**
> You sound like you only have Window VMs and no Linux guests yet?Right.  I have Linux as my primary OS.  There's no need for me to run virtualized Linux boxes.  (I don't do much experimenting with software... my computer is a tool, not a hobby).

You seem to be trying to do some pretty crazy things with your computer.  While you might be able to do it, I certainly cannot recommend your plan.  But its your computer... have fun. :)

---

