---
title: "I need Windows 7 on my Ubuntu 14.04 desktop"
date: 2014-04-26
forum: Virtualisation
---

### Post by Sherman_Willden on 2014-04-26
I need a windows host for a training program abut Windows Server 2012. I have a Windows 7 installation disk. Windows 7 blue screens with memory problems everytime I install it on my only computer. Ubuntu and BSD run all day long on this host. I have checked the memory using Ubuntu tools and the memory checks out OK. The disk utility tool shows 11 bad sectors. The computer specs are at the end of this post. Can I install a virtual Windows 7 on Ubuntu 14.04. How do I do it? I found [https://www.virtualbox.org/manual/ch01.html#idp53219184](https://www.virtualbox.org/manual/ch01.html#idp53219184). Are there any other virtual machines other than virtualbox? I hope I am asking the right question.

Memory 2.9 GiB
Processor Intel® Core&#8482;2 Duo CPU T8100 @ 2.10GHz × 2 
Graphics Intel® 965GM
OSType 64-bit
Disk 154.2 GiB
HP Compaq 6710b Notebook

Thank you;

Sherman

---

### Post by tfrue on 2014-04-27
Well, you could look into setting up a Xen hypervisor and have the option to set up other VMs.
[http://www.xenproject.org/users/getting-started.html](http://www.xenproject.org/users/getting-started.html)

I would stick to VirtualBox as it's super easy to use and can be installed on Window's and Linux which could be useful if you ever move to a Window's machine and could simply export and import VMs.

Chris

---

### Post by houstonbofh on 2014-04-28
That should be fine.  But the memory is quite lite...  How much are you giving the VM?  It needs 2 gig to boot...  And you need to be stripped down to low memory on the desktop...

---

### Post by jon43 on 2014-04-28
If you have 11 bad sectors, it's time for a new HDD. Unless you aren't storing anything of any value whatsoever on this system and are okay with later having to replace the disk and start from scratch without notice. 

A virtualbox install of Windows 7 is a piece of cake... but first you need to figure out what the disk issue is.

---

### Post by yan4 on 2014-04-29
> **jon43 said:**
> A virtualbox install of Windows 7 is a piece of cake... 
I wish it could be true for me.

:(

---

### Post by jon43 on 2014-04-29
> **yan4 said:**
> I wish it could be true for me.

:(

What sort of problems are you having? 

All you should need to do is install virtualbox from the software center, create a new virtual machine in the VB control screen, launch it and select either the ISO or insert your DVD into the DVD tray. When you're done, download guest additions and you'd be good to go....

---

### Post by yan4 on 2014-04-29
Jon, I think I JUST found the issue (as well the solution).

It was a very simple thing but that I believe may be annoying several people out there. I wasn't being able to install either W7 and WXP (as shown in [this]("http://ubuntuforums.org/showthread.php?t=2220777") thread), so I think it may be useful to share the trick.

Anyway, the problem is that after to boot with the install CDs the process just stuck at a screen sayin that there was a driver missing. If you are not absolutely sure that your CD is good you will think that it is messed up. Since I KNEW that my CDs were perfect (I have used them tons of times) it never passed in my mind, so I was sure that the problem was with Virtualbox.

Anyway, the solution is simple (after you know that). Whenever you experience the 'missing driver' experience, just go to the main screen of Virtualbox, click 'settings' (the yellow gear) of the problematic machine, then 'storage' in the list. then click onto the CD icon and ensure that the option 'Passthrough' is CHECKED. The problem is solved.

:)

---

### Post by jon43 on 2014-04-29
Good to know! Glad you got it working. 

I really don't know why anyone would dual-boot when there is such a wonderful option as running Win 7 in a VB!

---

### Post by Sherman_Willden on 2014-04-29
Thank you all. I am presently replacing the memory and then I will do the virtual steps.

---

### Post by jon43 on 2014-04-29
Bad sectors would be the disk, not the memory (ram)....

---

