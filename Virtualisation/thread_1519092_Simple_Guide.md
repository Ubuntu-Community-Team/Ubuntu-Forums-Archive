---
title: "Simple Guide"
date: 2010-06-27
forum: Virtualisation
---

### Post by birkopf on 2010-06-27
Can someone who has got experience with VMware post me some simple guide how to install vvmware on lucid 64bit please ?

I read through few how to's and I am more confused than before... :confused:
  
I have no experience what so ever with virtualisation and I am really afraid I will screw my system (again)

What I want to do is to install vmware so that I can install Blackberry Manager (which is designed for Windows) and run it under my Ubuntu 10.04.
Blackberry Manager requires Microsoft Framework and that's why I couldn't install on wine.

- Could someone help please ?

---

### Post by fjgaude on 2010-06-28
Download VMware Player 3.1.0 from the VMware site.

In the folder where this file is, the .bundle file, run:

> ./yourfolder/VMware-Player-3.1.0-261024.x86_64.bundle

After that runs you should have an icon on your desktop. From there you can following the menus to install Windows just as you would to a hard drive.

I think all the defaults will likely be what you wish. I only run 512 MB for WinXP and that is sufficient for all my graphic design work I do with Adobe products.

Let us know how you get along.

---

### Post by birkopf on 2010-06-29
> **fjgaude said:**
> Download VMware Player 3.1.0 from the VMware site.


I am downloading third time as vmware has got (IMO) unnecessarily complicated download system. File downloaded with error previous times and took me bit time to figure it out. Their server has got annoying behaviour of interrupting connection when I have 97% - 98% file


> **fjgaude said:**
> 
In the folder where this file is, the .bundle file, run:
> ./yourfolder/VMware-Player-3.1.0-261024.x86_64.bundle

I assume it will go by sudo sh as well.
When I was trying previously I got message back:

"magic number does not match"

but this time I will check md5sum to be sure file is not corrupted. 

> **fjgaude said:**
> 
I only run 512 MB for WinXP and that is sufficient for all my graphic design work I do with Adobe products.


Only 512mb? Installation of XP takes at least 3Gb
Do I need to partition hdd and create some windows system file like fat32 ?

---

### Post by birkopf on 2010-06-29
All was going well. I created virtual machine and started installing windows xp. System blocked. It was all running but I have lost my mouse and keyboard. I needed to restart. After restart I don't have Vmware icon in system menu. 

I found command to fire up vmplayer from Run Application menu. This time windows installed properly. 

Now I am trying to install blackberry manager. It may take me a while ( I need to read how to copy files to wmplayer, how to execute, etc)

Will come back as soon as there will be progress.

---

### Post by birkopf on 2010-07-01
I have done everything. Fjgaude thank you for help.

---

