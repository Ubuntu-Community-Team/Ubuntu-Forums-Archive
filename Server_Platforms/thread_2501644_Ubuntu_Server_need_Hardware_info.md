---
title: "Ubuntu Server need Hardware info"
date: 2024-10-15
forum: Server Platforms
---

### Post by draukagrissa on 2024-10-15
Hello,

I have an old Dell Poweredge R520 server.
It has 2 Zeon E5-2470v2 cpus.

Can Ubuntu Server be used with such an older cpu and system?

Ubuntu is not in the Dell specs for usable OS which is why I am asking.

Also With Ubuntu Server can VM's be made and used with it?

Last question, With Ubuntu Server can part of the system be used as a NAS?

Thanks
Drauka

---

### Post by sgt-mike on 2024-10-15
Before even glancing at the hardware ... Yes... yes... and yes ....... now for the other part within limitations of the hardware. Manage your expectations around the processor ram capabilities. The better the hardware the more capable the server is. Is your system capable?  yes, could that change to a no yes based on the type of VM's etc you wish to deploy. People run NAS , and media servers on NUC's so yeah it will work.

It's not uncommon for some of the folks on here to use 1 system as their VM, NAS/NFS, and media player in their home labs.


[https://www.dell.com/support/manuals/en-us/ubuntu-server/ubuntu_20.04_rn_pub/important-notes?guid=guid-29202b66-7368-413e-b4d7-44dcfce87ca2&lang=en-us](https://www.dell.com/support/manuals/en-us/ubuntu-server/ubuntu_20.04_rn_pub/important-notes?guid=guid-29202b66-7368-413e-b4d7-44dcfce87ca2&lang=en-us)


Also scroll down to where it list Linux operating system in a drop down you will see Ubuntu. although listed as Ubuntu Desktop if a system can run Desktop it can run Server.

[https://www.dell.com/support/home/en-us/drivers/supportedos/poweredge-r520](https://www.dell.com/support/home/en-us/drivers/supportedos/poweredge-r520)

With that R520 and two Xeon processors that you list I think you'll have 16 cores total. Linux will handle multiple cpus without issues. Is it doable yes. But you will need to research even further than the link's I provided. There is a ton of folks on here way more knowledgeable than I on such matters. Take your time plan it out, ask and actively listen. Hopefully someone else will chime in here.

---

### Post by draukagrissa on 2024-10-16
Hello SGT-Mike,

Thanks for the fast reply to my questions I really appreciate it.

Currently the system has Windows Server 2008 R2 on it.
But I Am currently trying to find a way to reset the password as I dont know it.
Previous owner asked me to Reimage the OS as he did not want to give me the password as he has stuff stored on the system.
I dont have a clue how to reimage it, and without the OS Disk which I am trying to locate online to buy I thought changing to Ubuntu Server would be the best option.

Thanks again for the help.
Drauka

---

### Post by sgt-mike on 2024-10-16
You might find this a interesting read
[https://www.dell.com/support/kbdoc/en-us/000130160/how-to-install-the-operating-system-on-a-dell-poweredge-server-os-deployment](https://www.dell.com/support/kbdoc/en-us/000130160/how-to-install-the-operating-system-on-a-dell-poweredge-server-os-deployment)

without getting wrapped up in all the verbiage that Dell uses, basically a bootable copy of a Linux server boot from USB and install. What I personally would check is if the controller can be set set to IT mode versus HW RAID. Then utilize the software Raid MDAM or Open ZFS to assemble the drives for data. Personally I prefer to stick the operating system on a separate hard drive not included in the raid. 

now I kind of got the cart before the cart fist handle the PERC from HW RAID to HBA / IT mode. Then use a small 64gb to 120 BG SSD to boot the OS and the other drives can be used either separately or assembled into software RAID 

You mentioned password can you access and control the BIOS without entering a password?

Perc to HBA (AKA IT) mode
[https://www.dell.com/support/contents/en-us/videos/videoplayer/how-to-convert-raid-mode-to-hba-mode-on-dell-perc/6079781997001](https://www.dell.com/support/contents/en-us/videos/videoplayer/how-to-convert-raid-mode-to-hba-mode-on-dell-perc/6079781997001)

[https://www.youtube.com/watch?v=s1awnmFW3kw](https://www.youtube.com/watch?v=s1awnmFW3kw)

[https://www.youtube.com/watch?v=y9b9IopSNBE](https://www.youtube.com/watch?v=y9b9IopSNBE)

---

### Post by draukagrissa on 2024-10-16
Hello,

Yes I can access the bios fine.
As for system password I found a post on how to reset it, if I find the dell server os disk.

Thanks for the help and the links.
Drauka

---

### Post by stephan4 on 2024-11-09
I see no issues.
Just because DELL does not mention anything, it does not mean it wont work.

---

### Post by LHammonds on 2024-11-10
I like to install Proxmox on old servers.  Then deploy VMs on it...such as Ubuntu Server.  However, you did not say how much RAM it has so it if only have 4GB RAM, I'd just install Ubuntu as bare-metal install.  But if it had 8 GB or more, I could easily run 4 basic Linux VMs on it with 1 or 2 GB each.

LHammonds

---

