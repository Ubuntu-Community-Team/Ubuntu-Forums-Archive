---
title: "Adding a new feature to the Graphical Install..."
date: 2012-04-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jmate24 on 2012-04-07
This is just a suggestion for those who are to "skiddish" about using the 12.04 Server Disk. My suggestion comes from a previous post I read here: [http://ubuntuforums.org/showthread.php?t=1949220&highlight=lvm+raid]("http://ubuntuforums.org/showthread.php?t=1949220&highlight=lvm+raid"). 

     In the Graphical X Desktop (of any version of 12.04) installer, make an available choice for RAID and LVM that automaticaly writes a gpt partition and partitions your aray as well as sets up a partity volume. then formats it with a 100MB boot FAT-32 and a small empty partition (no partition there approx.= 2MB = 2048KB after, which are both for the boot files [whether using UEFI or BIOS boot]. P.S. make the install disk detect UEFI or BIOS boot.
     Then lets you choose what you will be using the system for [i.e. NFS, Samba/Print server, NAS or a MMAS (multi-media attached storage), etc.].
     Next the installer "suggests" a partitioning design based on your choices (check boxes). Then you can either keep the suggested design or change it by going into the Manual Partitioner. 
     It is so that "we" (the community) can make and have things a little more unified when you install from either the Desktop/Alternate or Server install disk.
     It will make things easier for our "@Home Linux Enthusiasts" to build their own Servers with just a few clicks instead of having to use the "purple" OEM alternate/server installer or having to call or post for either userbase or tech help thus by saving them time and money.   
     Installing the documentation to create a server automatically in the install disk is vital for running a server instead of having to go on our favorite package manager, do a search and then install it.
     It can get very confusing knowing which documentation to install from Synaptic and especially for those creating a server for the very first time. So an Ubuntu Server Guide installed by default in the Ubuntu Documentation for Desktop install disk would be helpful.

As always it is easier to have a more unified ease of use across all install iso types than to have one that is more techincal than others. That way if it is necessary to use the Alternate/Server install disk then the user, client, company, and community can know what to expect from a great OS.

Thanks,
jmate24

---

