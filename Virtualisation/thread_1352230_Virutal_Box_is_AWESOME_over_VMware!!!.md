---
title: "Virutal Box is AWESOME over VMware!!!"
date: 2009-12-11
forum: Virtualisation
---

### Post by RazorV on 2009-12-11
I just have to say that VirtualBox is 110% better than VMware.  I followed the install directions for VirtualBox and the install went so smooth.  Can't say that for VMware.  Then i Installed the extras after I built my XP-32bit machine.  Absolutely incredible!  

What a awesome program!  I can't say enough about it.  Everything works right out of the "Box" ;) !  I have full Office 2007 running and some Adobe Apps (Indesign, Photoshop).  All instlaled fine and run.  And I will say, they run 50% faster using VirtualBox then VMware.  I can't see how in the world VMware can compete with VirtualBox.  But I guess there are some things that VMware offers that VB doesn't yet.

VMware - what a pain in the ***** to get that running!  Install a buch of crap becuase it can't compile for the kernel - yet it suppose to be for Linix!?!  Sound card only worked 1/2 the time, the darn mouse wouldn't focus correctly outside of 800x600 so you have to edit a file to get it to work, and the amount of resources that VMW took was way more than VB.  Furthermore, you have to use a web interface to get to the console.  Well that alone is a pain.  I installed some updates to Ubuntu 9.10 and guess what? I couldn't get to the VMware Server Console anymore.  What a pain in the butt!  VirtualBox just doesn't have any of these issues and it's way faster, and IMO, it's just awesome!

If you are looking to Install a Virtual Machine, go with VirtualBox!  Read the instructions at VirutalBox.org before installing and install the supporting libraries, add permissions for yourself to access all resources, install VB, add yourself to the Group (VirtualBox) and you are done!  Unless you have major specific needs that VB doesn't support I see no reason to go with the VMware.

I attached a pic of VB running XP in a window with Outlook minimized at the bottom just for looks.  I love this app! 

Just my .02 cents!

Cheers and Happy holidays to all!

Greg
Sarasota, FL

---

### Post by bluelamp999 on 2009-12-11
Hey Greg,

Couldn't agree with you more...

VBox is *much* faster than VMWare (especially running XP guests)

---

### Post by Ginsu543 on 2009-12-12
I've never tried VMware, but I too am WAY impressed with VirtualBox. It was easy to set up (for the most part) and things just worked out of the box, including internet/networking and all my usb devices. It's amazing to me that even utilities like Partition Magic and Diskeeper work on the virtual hard drive, let alone Microsoft Office and Photoshop. In fact, I am in the process of defragmenting the virtual hard drive as I type this. The only thing that doesn't work is graphic-intensive games. I can't believe a program like this is for free!

Here is a screenshot of my rig running Windows XP in VirtualBox (with an episode of The Big Bang Theory playing on Gom Player):

---

### Post by fjgaude on 2009-12-12
Well, over the years I've tried both and I'm with VMware Player 3.0 now. I can't tell the difference in speed with guest WinXP and native. Player permits up to four cores, has fast graphics, and support for just about any disk or USB port. Works as kernels change from 2.6.27 through 2.6.31. And it is free!

---

### Post by Dedoimedo on 2009-12-14
I would not blame VMware as much as you do.

The real problem is that Ubuntu ships with many components against the standard Linux conventions, which breaks VMware software, which is intended for the entire Linux base, with RH and SLE in the focus.

The fact you don't have xinetd on Ubuntu or do not use runlevels as expected is a problem that VMware cannot solve.

I've had to fight VMware when installed on Ubuntu since day one, never so with openSUSE or CentOS, it installs without a hitch.

That said, VirtualBox is a great program ... the comparison between the two should be made with the same reference, otherwise it's moot.

Don't forget that VMware software is the leading virtualization thingie in the market. VMware console also lets you connect remotely, very easily. VirtualBox still has a registration issue on proxied systems. No screenshot or video capture feature yet either.

The problems you mention are specific to your setup and not something that you should generalize across the entire usage model. Performance is roughly the same in both.

Dedoimedo

---

### Post by scrooge_74 on 2009-12-14
Virtualbox is a great tool for using at home or a small office, but I think if you plan to have a couple of big servers running a big database it would be better to use VMware for it. That said I see Sun doing a great job with Vbox to go catch the others in the market.

I like VBox capacity to run from the command line and no need to use the GUI to run virtual machines

---

### Post by RazorV on 2009-12-14
I guess I somewhat agree with [Dedoimedo]("http://ubuntuforums.org/member.php?u=316632").  IMO, VMware should make a version for Ubuntu instead of assuming that people will know how to "make it run" on different versions of Linix.  I feel Ubuntu is very widely used more than any other version of Linix (i could be wrong here) and VMware, IMO, should develop a version specifically for Ubuntu.

Regardless of the above, VirtualBox runs circles around VMware on my machine.  VMware so very slow and my sound card only worked half the time.  Then I couldn't get into the VM console on one occasion.  Yea VMware may offer some very technical advantages, but for the average user or average power user that doesn't need all the crap that VMware needs to install to run properly, Virtual Box is a much better choice, lighter on resources, works right out of the box without having to edit all kinds of files, doesn't neet to load a ton of libraries or supporting libraries/files just to compile the kernel.  And it's faster on my machine.  

Anyway, to each their own.

Cheers,
Greg

---

### Post by benjaminsuman on 2009-12-14
This isn't really a fair comparison.  With the exception of VMware Fusion for Mac, VMware's products are aimed at enterprise level deployments centered around the vSphear 4 platform.  All of their programs, VMware Player, VMware Workstation, VMware Server, etc, are designed to facilitate developing and moving VMs to run on high powered systems dedicated to running as Virtual Machine Hosts.

Virtual Box, while it is slowly gaining some enterprise features like live migration, is a long ways from being even in the same class as VMware.  Really, if you want to compare Virtual Box to anything you should be comparing it to Parallels Desktop.

---

### Post by jigyb007 on 2009-12-26
I am having huge problems getting VMware to work in ubuntu. I see by cruising these forums that people mention try to use 1 core instead of 2 in the config. I did that and still have problems. I have no issues in VirtualBox. However, I wish I could get vmware to work as well, as I much rather use that. I have 5 gigs on ram using a intel core2 duo at 3.2 Ghz, so I don't think my computer lacks the performance to run this. I am trying to run Windows XP and it runs super slow. In virtual box it runs as fast as it almost does running natively. 

Has anyone had success running windows on VMWare in ubuntu without speed issues ? 

As far was going VMware on mac goes...I have to disagree. On mac using parallels blows VMware out of the water...performance and features wise. VMware runs to sluggish IMO..I could be doing something wrong in my setups though. But running windows on a MAC via parallels works amazingly fast for a Virtual machine. I have yet to have any issues...

---

### Post by coskierken on 2009-12-28
How about letting us know which version of VMWare you are running when you bash it.  I know for a fact VMWare Workstation 7 works 'out of the box' with 9.10.  I have loaded both VirtualBox and VMW 7 and prefer VMW 7 in speed and ease of use.  If you have not tried VMW 7, download the trial version and give it a shot.  You might be surprised.  Oh, don't forget the Unity button!

---

### Post by 32034 on 2009-12-28
I made the switch over about a year ago and have yet to regret the decision, except some issues with running Virtual Box on my Windows XP desktop and trying to run OpenBSD guests. FreeBSD runs fine, it's just OpenBSD has issues with installing. Maybe I'm behind on an update.

---

### Post by RazorV on 2009-12-28
> **coskierken said:**
> How about letting us know which version of VMWare you are running when you bash it.  I know for a fact VMWare Workstation 7 works 'out of the box' with 9.10.  I have loaded both VirtualBox and VMW 7 and prefer VMW 7 in speed and ease of use.  If you have not tried VMW 7, download the trial version and give it a shot.  You might be surprised.  Oh, don't forget the Unity button!

You may be right but VMW7 is also $189 US Dollars where as VirtualBox is FREE! 

Big difference.

---

### Post by fjgaude on 2009-12-28
The last time I looked Workstation 7.0 was $99.00. Player 3.0, which does everything, like make new VMs, handles just about everything except read down the LAN is totally free and works with all the versions of Ubuntu, out of the box. Both are very sweet VMware products.

---

