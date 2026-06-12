---
title: "VirtualBox Windows7 won't start"
date: 2015-01-06
forum: Virtualisation
---

### Post by chris137 on 2015-01-06
Hi,
I am running linux and windows 7 as dualboot.
Since I very rarely use windows I tried to access it by starting it with VirtualBox.
These are the steps I took:
[LIST]
[*]Installed VirtualBox 
[*]Entered this code to create a file pointing to my harddrive where sda6 is the partition windows is on:```
**sudo VBoxManage internalcommands createrawvmdk -filename "windows.vmdk" -rawdisk /dev/sda6**
``` 
[*]Created new virtual machine with **windows.vmdk** as source 
[*]Started the machine 
[/LIST]

Sadly it won't start and I have no idea why.
I run VirtualBox as sudo since I do not have permission to use the vmdk-file as user (VERR_ACCESS_DENIED)

Last log is this:```
00:00:02.968116 Guest Log: BIOS: Booting from Hard Disk...
```From there it won't go further.

I am running linux from the same SSD. Might that be part of the problem?

---

### Post by TheFu on 2015-01-06
If the virtualbox HW environment doesn't match the real HW environment of the system, this won't work with Windows, sorry.

All the major devices presented need to match - that is a Windows thing.

Basically, it appears to your Windows install that you've swapped 
* the motherboard
* the sata controller
* the network card
* the northbridge
* the southbridge
* and the video card.
Windows just can't deal with it. It demands a fresh installation.

---

### Post by chris137 on 2015-01-06
Well.. damn you windows :D

Any other related way to accomplish this?
Main reason I wanted to do this is that all my data already is there :P
Also that version would be activated which I am not sure would work on the VM.

If there is no way whatsoever I'll start tomorrow to install a fresh windows.
Will be a little more work but still better than rebooting and leaving linux.

---

### Post by TheFu on 2015-01-06
If all you want is to access the data, why not just mount the NTFS storage from inside Linux? 
Am I confused? This is standard stuff and has worked for ... like 20 yrs.  Many how-tos exist for this, if you need that. Pretty much every Ubuntu book written will have instructions too.
[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) has links to beginning Linux folks for learning stuff like this.

---

### Post by chris137 on 2015-01-06
No, no.
I really want to boot on windows.
What I meant to say is: The windows on my drive already is configured, got my files, links and so on.
Please focus on running windows with a VM or similar.

---

### Post by fizbaum on 2015-08-26
Hello,

I know, this thread is a bit old, but I want to give an answer:
It is possible to boot an already existing Win7 in Virtualbox. It is also possible to avoid reactivation by making the virtual hardware similar to the physical hardware. 
I wrote a german manual about this:[ https://wiki.ubuntuusers.de/Dualboot-Windows_virtualisieren]("https://wiki.ubuntuusers.de/Dualboot-Windows_virtualisieren?highlight=dualboot%20windows%20virtualisieren"). If you have problems with it, you may ask me, I will see what I can help.

---

### Post by TheFu on 2015-08-26
Very cool for bleeding edge types!

It should be noted the steps are non-trivial with multiple points where harming the boot for the entire box can happen, not just the VM.

On a scale of 1-10, this is a 9. As a reference, getting VGA passthru working under KVM/Xen would be about a 7 in comparison.  IMHO.  Loading Win7 into a VM (KVM/Xen/Virtualbox) would be a 1-2.

Of course, my 3 yrs of German training 25 yrs ago wasn't that good to start and the google translation was not always clear - especially about the need to re-authenticate from MSFT.

Regardless - very cool.  And be very careful.

Or did I misunderstand?

---

### Post by fizbaum on 2015-08-26
Hello TheFu,

yes, at some points it is critical to do the right thing, otherwise  there can be done a lot of damage. But also I can say, the manual was  tested by many (dozens? hundreds?) german users with no problem. If  every step one by one is done right, nothing bad can happen. (Except, I  heard of one case, when ubuntu crashed while Win was running in VBox -  Win was damaged after that. On the other hand, ubuntu crashes nearly  never, so the danger is really small)
Although the manual is very long, there are only a few really steps to do:
 * create raw disk access (for more security: access is limited to  windows partitions, and a virtual mbr instead of the real mbr is used to  protect GRUB)
 * set permissions (small udev rule)
 * make virtual hardware similar to physical hardware (trivial, but a lot of small steps)
 * run Win7
I would be happy if someone (maybe you?) would like to make an english  translation of the manual; my english is not good enough to do that, I  could only check if the translation is right.
Right now, the manual contains only the way for legacy BIOS systems, but  UEFI is possible,  too, with only a few things to change.

edit: the greatest danger is to boot the host ubuntu as a guest - that would destroy ubuntu. In the manual there are some steps to avoid this for sure.
edit2: > and the google translation was not always clear - especially about the need to re-authenticate from MSFT.
The virtual hardware can be made similar enough to the physical hardware, so you don't need to re-authenticate windows.

---

