---
title: "Troubles trying to run Ubuntu inside Vmware Server"
date: 2007-11-20
forum: Virtualisation
---

### Post by BVStang1967 on 2007-11-20
Hello, I was running Ubuntu on its own partition dual booting between ubuntu and xp.  Due to the programs I have to use for my design classes I need to be in xp all the time now.  I attempted running ubuntu inside vmware server by creating a virtual machine and booting it with a text install disc in the cdrom drive. Everything would appear to be installing fine but then it would just freeze at 90% and wouldn't do anything else.  Does anyone know of a step by step tutorial that would get ubuntu to install inside a VM? Thanks.

---

### Post by AlanRogers on 2007-11-20
I've been trying to do the same with Linux Mint 4.0 and it wouldn't install. I've reverted to 2.2 and will dist-upgrade until I get to 4.0 - Yes, painful, but it's good practice at using VMWare Server!
 
Which version of Ubuntu? Are you using the Alternate CD? Have you considered using the Dapper version and going from there?

---

### Post by rmemm on 2007-11-20
You should be able to install it directly from the ISO.  VMWare can connect to an iso image file.  I can't remember if I installed my image using VMWare Server or VMWare Workstation -- but I do run it on VMWare server.  

I don't know why it hung.  You might want to check your memory and disk space allocation that you gave the VM when you configured it.  You should probably have 8 GB (4 GB minimum) in the virtual disk, and at least 512MB of virtual memory assigned to the VM.  Also if your virtual disks are on a FAT volume (not NTFS), then make sure the disks are configured to segment (remember FAT is limited to 2GB files or something like that).

You can do a similar thing with qemu which is open source -- but not a pretty.

Might want to check your image also to see if it's corrupt.

Also, the company behind VMWare does have prebuild VMs you could just download and run -- I actually build my own -- but you don't really need to.

Rob

---

### Post by AlanRogers on 2007-11-21
Will mounting an ISO as a virtual CDROM run faster than sticking the burned CD in the actual drive? I've got all the ISOs on my Ubuntu machine and I'm building virtual machines from CDs that I've burnt, in VMWare Server, running on the same box! :oops:

---

### Post by coolguy2006delhi on 2007-11-21
Ya , when you insert iso image , it directly reads from your harddrive instead of cddrive and therefor data transfer rate is much faster. Also I would recommend you to install Ubuntu on seprate partition rather than on the virtual machine, as my experience is really bad with it.

---

### Post by AlanRogers on 2007-11-21
> **coolguy2006delhi said:**
> Also I would recommend you to install Ubuntu on seprate partition rather than on the virtual machine, as my experience is really bad with it.
Thanks for confirming that; I thought it might be the case. Can you expand on what you meant above though? My virtual machines are on an entirely separate hard drive from my Ubuntu installation. Is this what you're recommending?

---

### Post by rmemm on 2007-11-21
I think the suggestion was to use real hard drive particians rather than visual disks (which are mapped to files). 

I don't know myself how much better this is -- but one would think performance would be a bit better.  Also probably depends on your file system your using on the host OS -- people complain ext3 is not so good for large files.  Maybe that causes some VMWare performance hits on virtual disks -- I'm just speculating.

It would be good to have some clearification though.

Other thing I would add -- if you do decide to use real hard drive particians -- be very careful -- it's very easy to destroy one of your valuble/good partitians by mistake if your not careful during setup.

Rob

---

### Post by rmemm on 2007-11-21
Sorry I meant "virtual disks" not "visual disks" above.

Rob

---

