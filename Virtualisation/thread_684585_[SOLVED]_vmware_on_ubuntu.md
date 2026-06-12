---
title: "[SOLVED] vmware on ubuntu"
date: 2008-02-01
forum: Virtualisation
---

### Post by aBitLater on 2008-02-01
Hello,

As I write this, I'm finding viruses on my windows laptop.  I'm ready to, pardon the pun, boot windows (out the door!).  But, for my business, I need to run Peachtree Accounting, and MS Money (for the wife).  And, I use MS Visual Studio, SQL Server, and MASM in a development environment.

1.) So, can I install ubuntu / gutsy on my laptop without hiccups (HP Pavillion dv8000) ?

2.) Can I use VMware Server or Xen to install Windows XP on top of Ubuntu (sorry, not sure I know the vmware / xen terminology here), and USE all these programs mentioned above?

3.) If I create a 'virtual guest' OS for winxp to keep our personal data, and another winxp virtual guest for development (where I am learning about ethical reverse engineering and use tools that are sometimes 'suspicious'), will my programs and files in the first guest winxp be completely safe from the other winxp virtual machine.

Note: I do not need both virtual winxp's to run at the same time.

Thank you!

---

### Post by emarkd on 2008-02-01
1.  No idea, sorry

2.  Absolutely.  I use VMWare because it can boot a real partition,meaning I can have XP from within Ubuntu (I also use it for .NET programming) or I can boot it directly on the hardware (for the occasional 3D game).  If you really want to install Windows on virtual disks, lots of people like VirtualBox, so it may be worth looking into.

3.  Sure, you can create as many virtual disks as your real disk can hold and they're completely separate from each other.  You can even run them at the same time if you've got enough processor/ram to keep up.

---

### Post by Het Irv on 2008-02-01
As a rule of thumb If the computer can run the Live CD well chances are that it will run from the disk just as well.  There are time when this is not true but for the most part it works.  

Just in case here is the link to Download the Live CD
[http://www.ubuntu.com/getubuntu/download]("http://http://www.ubuntu.com/getubuntu/download")

---

### Post by aBitLater on 2008-02-01
> **emarkd said:**
> 1.  No idea, sorry

2.  Absolutely.  I use VMWare because it can boot a real partition,meaning I can have XP from within Ubuntu (I also use it for .NET programming) or I can boot it directly on the hardware (for the occasional 3D game).  If you really want to install Windows on virtual disks, lots of people like VirtualBox, so it may be worth looking into.

3.  Sure, you can create as many virtual disks as your real disk can hold and they're completely separate from each other.  You can even run them at the same time if you've got enough processor/ram to keep up.


thanks for the help!  


1.) So, do I have to create the partition for the guest winxp when I install ubuntu (which will be my main OS)??  How much space for the winxp operating system and ISO, if it's needed, should I allow (including the never ending hotfixes and service packs :) )
.  
When determining the size of all my other apps I will need, is it best to view the sizes of the app folders in Program Files directory.  And how much unused space should I allow to keep things running efficiently in Windows?

2.) Booting to the guest OS directly (winxp) under vmware, for games - is that the free vmware server that can do that?

3.) Can someone tell me here, or point me to a good article on partitioning ubuntu during setup so that I can have as much disaster recovery protection as possible (keep my home directory if possible).  I'm not sure how many partitions to create, and what sizes they should be.  On my current ubuntu desktop, I seem to recall that it created one partition "/" for newbs like me.  On my current ubuntu machine, I have installed LOTS of stuff from synaptic just out of curiousity (and I assume this isn't all getting installed to my user directory since I have to 'sudo' synaptic.

Other items I might want to be able to restore quickly on ubuntu if something goes wrong down the line,are  MySQL, and Apache2

---

### Post by aBitLater on 2008-02-01
> **Het Irv said:**
> As a rule of thumb If the computer can run the Live CD well chances are that it will run from the disk just as well.  There are time when this is not true but for the most part it works.  

Just in case here is the link to Download the Live CD
[http://www.ubuntu.com/getubuntu/download]("http://http://www.ubuntu.com/getubuntu/download")

Thanks!

I'll try it out.

---

### Post by emarkd on 2008-02-01
I think you misunderstand.  You have two choices:

1.  Install Windows and Ubuntu next to each other in a dual-boot scenerio, both on partitions of your real disk.  You can choose to boot directly into either one.  Then, VMWare running in Ubuntu can boot that Windows partition and run it in a Virtual Machine.  I'm simplifying, but it's quite possible.

2.  Install Ubuntu on your computer, then use VMWare to create a virtual disk and install XP on that virtual disk.  It has nothing to do with your real disk - it's actually one big file that VMWare uses like it's a real disk.  You can't boot directly into Windows without having Ubuntu running.  This is fine for almost everything except 3D games, because VMWare emulates the hardware that Windows sees.  You may have a $400 video card, but VMWare just emulates a basic VGA card that doesn't support DirectX.

Does that make sense?

---

### Post by aBitLater on 2008-02-01
Thanks for the clarification emarkd

so on my current ubuntu machine which is already a dual boot machine to windows xp (on a separate drive), I can still do this?  

on my laptop, I don't care about 3d gaming, so I'll investigate VirtualBox a little more, on your recommendation.

---

### Post by HermanAB on 2008-02-01
Uhmm, if you boot Windows natively *and* from VMware, then the registration may get confused and you may end up in a situation where you have to re-register Windows every time you boot.  This will drive you bonkers in no time flat.  It is better to do it one way and stick to it.

The other solutions are either The Pirate Bay for a cracked copy of WinXP, or the latest version of Wine from Codeweavers ([www.codeweavers.com](www.codeweavers.com)), so that you don't need WinXP anymore.

In my experience, the less MS software you use, the less your computer troubles will be.  The only way to get completely trouble free computing, is to avoid MS software altogether.  However, running Xp in VMware Server only when needed, is a good trade off, since you can easily back-up a VM - just make a tar ball of the thing and save it on a DVD.

Hope that helps!

Herman

---

### Post by emarkd on 2008-02-01
Sure, you can boot that Windows partition using VMWare.  There's quite a few things to do, though.  [Here's]("http://oopsilon.com/Running-a-Windows-Partition-in-VMware") a good walk-through.  It's written for Gentoo users so the installation stuff may not apply, but the actual setup stuff is the same.

One thing I'll mention that the tutorial doesn't is that your Windows installation will think you've moved it to a new computer and some software may bug you about activation.  I've never had XP actually do this, but Office is terrible about it.  Also, be sure you keep up with the state of that Windows installation.  A few times I've booted Windows directly on my hardware while I had previously suspended it in VMWare.  The journaled filesystem in XP doesn't like that at all and you'll spend a few hours letting chkdsk run if you make that mistake. ;)

---

### Post by aBitLater on 2008-02-01
ok, thanks guys for all the input.  

I'm now going to search for thread on partitioning schemes... if anyone here has a good link, please let me know.  Otherwise, this thread has cleared up quite a few things for me!

---

