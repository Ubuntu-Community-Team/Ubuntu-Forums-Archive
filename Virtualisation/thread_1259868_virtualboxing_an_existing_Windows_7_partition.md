---
title: "virtualboxing an existing Windows 7 partition"
date: 2009-09-06
forum: Virtualisation
---

### Post by rikkyc on 2009-09-06
hi all,

i'm pretty new to linux, so forgive me if i sound like an *******.
i'm actually running mint 7, which is a variant of jaunty so i think jaunty advice would still be relevant.

i obtained the latest version of VB directly from the website (3.0.4 i think) and it runs fine.
i'm wondering if there's a way in which i can run my existing Windows 7 installation from within VirtualBox without having to do another install.

my current partitions are setup as so (single internal HDD / sda):
Windows / sda2 (NTFS) 64GB
Media / sda1 (NTFS) 160GB
Mint / sda4 (EXT3) 10GB
Swap / sda3 (SWAP) 1GB
none are logical

any help would be great.

---

### Post by quixote on 2009-09-07
I run vbox, but I'm not an expert.  *As far as I know* vbox can't do this.  It's one of its shortcomings compared to vmware, I believe.  

I've often thought that it would be really nice if you could just point vbox toward an install.  Seems like it shouldn't be that difficult!

---

### Post by Ocxic on 2009-09-08
Yes you can give VBox direct access to your drive, or even a certain partition, but it is not recommended to switch between the virtual environment then boot the drive normally as it will disrupt the reference file vbox will use for your drive.

more info are in the vbox manual available from the vbox website

---

### Post by dk06 on 2009-09-08
> **rikkyc said:**
> hi all,

i'm pretty new to linux, so forgive me if i sound like an *******.
i'm actually running mint 7, which is a variant of jaunty so i think jaunty advice would still be relevant.

i obtained the latest version of VB directly from the website (3.0.4 i think) and it runs fine.
i'm wondering if there's a way in which i can run my existing Windows 7 installation from within VirtualBox without having to do another install.

my current partitions are setup as so (single internal HDD / sda):
Windows / sda2 (NTFS) 64GB
Media / sda1 (NTFS) 160GB
Mint / sda4 (EXT3) 10GB
Swap / sda3 (SWAP) 1GB
none are logical

any help would be great.


**[Importing an Existing Windows XP Installation into VirtualBox]("http://www.justsoftwaresolutions.co.uk/general/importing-windows-into-virtualbox.html")**

**Wednesday, 03 June 2009**

[B]
[http://www.justsoftwaresolutions.co.uk/general/importing-windows-into-virtualbox.html](http://www.justsoftwaresolutions.co.uk/general/importing-windows-into-virtualbox.html)[/B]

---

### Post by quixote on 2009-09-09
I am really glad to know about that!  Thanks for the links, too.

---

