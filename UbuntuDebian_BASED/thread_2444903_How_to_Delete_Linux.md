---
title: "How to Delete Linux"
date: 2020-06-05
forum: Ubuntu/Debian BASED
---

### Post by ivan23m on 2020-06-05
How do you delete linux? I came to this point:

```


ivan@ivan-desktop:~$ sudo fdisk /dev/sda1
[sudo] password for ivan:                 

Welcome to fdisk (util-linux 2.31.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

The old ext4 signature will be removed by a write command.

Device does not contain a recognized partition table.
Created a new DOS disklabel with disk identifier 0x0c46d6de.

Command (m for help): m

Help:

  DOS (MBR)
   a   toggle a bootable flag
   b   edit nested BSD disklabel
   c   toggle the dos compatibility flag

  Generic
   d   delete a partition
   F   list free unpartitioned space
   l   list known partition types
   n   add a new partition
   p   print the partition table
   t   change a partition type
   v   verify the partition table
   i   print information about a partition

  Misc
   m   print this menu
   u   change display/entry units
   x   extra functionality (experts only)

  Script
   I   load disk layout from sfdisk script file
   O   dump disk layout to sfdisk script file

  Save & Exit
   w   write table to disk and exit
   q   quit without saving changes

  Create a new label
   g   create a new empty GPT partition table
   G   create a new empty SGI (IRIX) partition table
   o   create a new empty DOS partition table
   s   create a new empty Sun partition table


Command (m for help): p
Disk /dev/sda1: 111,8 GiB, 120031543296 bytes, 234436608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0c46d6de

Command (m for help): d
No partition is defined yet!
Could not delete partition 1

Command (m for help): 


```


The reason I want to delete Linux is that I'm having some problems, I'm not sure hardware of software, and I want to install Windows alongside it but when booting my keyboard is unresponsive so I can't press any key when it says to press any key to boot from CD. It just boots straight into Linux.

Thank you

---

### Post by guiverc on 2020-06-05
You don't need to delete Zorin (which is not Ubuntu, nor a flavor of Ubuntu), you just install windows and it'll overwrite Zorin identically to if it wasn't there.

---

### Post by ivan23m on 2020-06-05
Like I said above. I am unable to start a Windows installation from CD. When booting it says to press any key to boot from CD but I can't do that, my keyboard is unresponsive during the boot process. Instead of starting a Windows installation it boots to Linux. So the only option is to delete Linux and then I'll be able to install Windows. I've found something. Should I click on ''Delete this partition'' on Settings > Disks or perhaps ''Unmount selected partition'' before deleting it with fdisk?

---

### Post by guiverc on 2020-06-05
Your issue is hardware or firmware related in my opinion, ie. you need to press a key message is from the windows install media to start it (or from BIOS/firmware). If you don't press a key, and you've removed whatever is installed on your hdd/ssd (*which windows will overwrite anyway during install*), you'll get a boot failure and a message to insert media & press a key to retry (*or whatever message your firmware has encoded to display*).

Removing the partition will just brick your machine I suspect.  Your best fix is via UEFI/BIOS change to allow the keyboard to work (ie. hardware/firmware change).

Your image looks like you've started `gnome-disks`, but being Zorin that I'm not really familiar with I won't advice sorry. Your mouse appears to be over "*Unmount selected partition*" but I'm guessing.

---

### Post by ivan23m on 2020-06-05
The keyboard part, although important, is not the main focus of this thread, rather it is how to delete Linux using fdisk. I have already copied the point on terminal I came to so I'm asking for advice on what to do next. After the "d" command what it should ask me (from my very limited understanding acquired through googling) the number of partition I want to delete but instead I got the message " No partition is defined yet! Could not delete partition 1".

The way I installed Linux was the usual way. ISO file, burned on CD, inserted it, no need to press a key for Linux to show up and you install it. I'm having some other potential problems with it, Linux, so I wanted to install Windows but now, all of a sudden, I put the ISO file Windows CD and it asks me to press a key to boot from CD. I read a few minutes ago that's a feature of Windows bootable CDs. 

I'm assuming you said that removing the partition will leave my PC bricked because I'll be left without a system and I can't press the key to install a new one, this time Windows, right? I don't think it'll get bricked because I don't have problems with installing Linux, I can just install a new one.
It's only the Windows I'm having problems installing currently.

Two main questions, how do I proceed with deleting a partition using f disk?  
And you wrote, " Your best fix is via UEFI/BIOS change to allow the keyboard to work". What are the steps to do that?

---

### Post by ivan23m on 2020-06-05
I've managed to solve the keyboard not working during the boot part. Immediately at the start of boot I pressed Delete to enter setup, chose "Integrated Peripherals", then marked "USB Keyboard Support" as enabled. And that was it, the keyboard works during boot, you can press a key to start the boot from CD. I still don't know how to uninstall Linux but it was answered that it's not necessary, it'll overwrite the existing system. The question from the title hasn't been answered, but I've got this breakthrough with the keyboard, should I mark as solved? If you wish you can respond to my question about how to proceed with Linux uninstall, maybe someone will find it useful but I think I might not need it anymore.

---

### Post by SeijiSensei on 2020-06-05
If Linux was residing on the partition that Linux names /dev/sda2, you could reformat the partition and overwrite whatever is there with
```
sudo mkfs -t ext4 /dev/sda2
```
Boot from an Ubuntu CD/DVD in "Try Ubuntu" mode, then run that command.

You could choose ntfs or vfat instead of ext4.  If you go that route, you probably want to mark the partition as holding the type of filesystem you intend to put there.  In fdisk, use "t" to pick a type. Use "l" to show the list of types.  When you're done, make sure to choose "w" to commit your changes to the device.

There are also ways to write zeros to the entire partition or other more intensive ways to delete its contents. Reformatting it will certainly do the trick.

---

### Post by guiverc on 2020-06-06
In bricked I meant that it won't work by itself (due to no OS), not that a new OS cannot be installed on it.  A poor choice of words on my behalf, sorry.

---

### Post by rbmorse on 2020-06-06
fdisk will do what you want, but when you invoked it above you told it a partition was a disk (fdisk /dev/sda1). 

Try invoking it with the command: 

sudo fdisk /dev/sda
 
and see if that works better.

---

### Post by ivan23m on 2020-06-06
This is what I did, as Seiji suggested above:

```


mint@mint:~$ sudo mkfs -t ext4 /dev/sda
mke2fs 1.44.1 (24-Mar-2018)
Found a dos partition table in /dev/sda
Proceed anyway? (y,N) 


```

Also, as rbmorse suggested I wrote sda instead of sda1. Is this going to delete the installed system, Zorin?

I`m booting with Mint, I`m having problems with Zorin, I`m gonna deinstall it. 

And yes, I know I can just overwrite the installed system, I`m asking in case I want to use the command in the future.

---

### Post by SeijiSensei on 2020-06-06
I don't think that's what you want. 

Does the device have partitions? If so, you want to format them like

```
sudo mkfs -t ext4 /dev/sda2
```

not /dev/sda which refers to the whole device. If there's stuff in other partitions on that drive you care about, I hope it's backed up.

---

### Post by rbmorse on 2020-06-06
*** withdrawn ***

I agree that formatting the partition is probably a better solution that outright deleting it.

---

### Post by ivan23m on 2020-06-07
It has only sda1 which you can see in my first post and no, I don't have anything of importance on the system, I've installed it a few days ago.

I guess I don't understand why would I leave a part of the system, a certain partition, when I don't need it and my goal is to delete the entire system and install a new one.

And I repeat, I know I can overwrite the existing system with a new one, installing a new one will delete the existing one, but I would still like to know how to do this command properly.

---

### Post by CelticWarrior on 2020-06-07
> **ivan23m said:**
> And I repeat, I know I can overwrite the existing system with a new one, installing a new one will delete the existing one, but I would still like to know how to do this command properly.

And I repeat what others have said, maybe not so explicitly, that likely you still don't know what you want and are chasing a non-solution for a non-problem. OSes aren't really deleted in the same sense we'd use the term "delete" when referring to files, folders and even entire partitions.

If the intention is to sell/give away a certain drive and you're concerned with private data there are tools for wiping it. Those have little to nothing to do with the partitions in the said drive, system or data partitions, it really doesn't matter.

If the intention is to install a different OS its installer likely will do everything that's needed for you. And very likely will also give you the option to reuse previous partitions and/or reformat, delete, resize and/or create new ones. Any Ubuntu installer (live USB or live DVD) comes with GParted (or some DE specific equivalent tool), a convenient GUI tool for managing partitions. With the aforementioned tool you can also totally blank any drive with a couple of clicks (Device menu > New partition table).

---

### Post by rbmorse on 2020-06-07
If your really, really want to delete that partition, you can use fdisk like this (assumes the partition to be deleted is the first on /dev/sda. Adjust as required):

sudo fdisk /dev/sda

press the "d" key to delete partitions.  Fdisk will tell you the partitions it finds on the device (1, 2, 3, etc.) and ask which you want to delete.  

In this case, press the "1" (numeral one) key.  Fdisk will report the partition has been deleted. 

Then press the "w" key to write the change to the disk.  Fdisk will report the partition table had been changed and quit.

---

### Post by ivan23m on 2020-06-08
What I want is to install Windows on this SSD to see if the problems I'm having currently with Linux, not only with this flavor, will show up again. I'm assuming no because I already have a drive with Windows and everything functions well. But that's a topic for another thread.

> **CelticWarrior said:**
> 

If the intention is to sell/give away a certain drive and you're concerned with private data there are tools for wiping it. 



The intention was to install Windows. 

"If the intention is to install a different OS its installer likely will do everything that's needed for you."

I know. I wasn't able to boot into one, the Windows installer. I needed to press a key to do that and my USB keyboard during boot was disabled. I thought I could go around that by removing the system that is currently installed, Linux, and then it will start, and that the way to do that was via terminal. When I solved the keyboard part, this became unnecessary. Maybe it was unnecessary all along. I don't know. 

When I wrote: 

"The question from the title hasn't been answered, but I've got this breakthrough with the keyboard, should I mark as solved? If you wish you can respond to my question about how to proceed with Linux uninstall, maybe someone will find it useful but I think I might not need it anymore."

I meant there that the question about removing it first instead of just overwriting it hasn't been answered at that point and someone might find it useful so you can explain how to do that. 

I'm satisfied with the level of details you gave in your responses, thank you all.

P.S. And I'm sorry, I don't know how to quote from different replies or is that possible at all.

---

### Post by CelticWarrior on 2020-06-08
> Maybe it was unnecessary all along. I don't know.

Unnecessary because totally irrelevant and you should know now because it was explained multiple times. The ability or lack thereof of booting an external media has nothing to do with the installed OS, if any. It's OS installation 101. Hopefully now you understand better the contents and tone of some of the replies above. Good luck with Windows (you'll definitely need it).

---

### Post by ivan23m on 2020-06-09
This post is referring exclusively to the last post.


Being a PC user requires dealing with multiple intricacies, the number of which would be enough to fill a dozen of books. To help with this there are experienced users and experts. For every branch of human knowledge and technology there is a majority that is a layman and there is a minority that is experts. If users of a certain technology knew everything about it expert advice wouldn't be necessary. 


Also, I'm pretty sure that the majority of PC users aren't acquainted with OS installation 101 let alone terms like live USB or live DVD (not necessary to explain it, I'm just stating an example).


The term "tone" I think can be used in the context of your response which contains responses like " Unnecessary because totally irrelevant and you should know now because it was explained multiple times.", " It's OS installation 10", and especially in the parenthesis " Good luck with Windows (you'll definitely need it)". This response, especially the thing written in the parenthesis, sounded condescending. It's sometimes hard to judge someone's intentions only through written word so if I misjudged you, It wasn't intentional.

---

### Post by CelticWarrior on 2020-06-09
> **ivan23m said:**
> Being a PC user requires dealing with multiple intricacies, the number of which would be enough to fill a dozen of books. To help with this there are experienced users and experts. For every branch of human knowledge and technology there is a majority that is a layman and there is a minority that is experts. If users of a certain technology knew everything about it expert advice wouldn't be necessary. 


We're in agreement, 100% :p

> Also, I'm pretty sure that the majority of PC users aren't acquainted  with OS installation 101 let alone terms like live USB or live DVD (not  necessary to explain it, I'm just stating an example).

Again, agreed. The vast majority of users really aren't acquainted with OS installation 101, live/installation media and so on. But those users aren't installing OSes, they are just using them to run their software. They may occasionally install additional software, muck about with a few settings but that's it, really. 

OTOH, you ARE installing OSes, Linux based and Windows, for that matter. You don't need to be a mechanical engineer or a mechanic to drive a car but if repairing, maintaining or tuning it, then you better know what you're doing.

Your question showed your knowledge of the matter - OS installation and/or multi-booting - to be insufficient but also totally expected because the believe about "deleting an OS to install another" is quite prevalent. So, this wrong idea is something we've seen here and elsewhere too many times already. Not a problem, that's what we're here for. And post #2 explained it already: *You don't need to delete Zorin (which is not Ubuntu, nor a flavor of  Ubuntu), you just install windows and it'll overwrite Zorin identically  to if it wasn't there.* This is the answer to your question, nothing else to add. The other issue is unrelated, obviously, and it triggered and unnecessary back and forth making the thread much longer that it should be because, again, the basic knoweledge about hardware and firmware (BIOS/UEFI) needed, IMO, for anyone installing OSes in PCs wasn't there. What I mean by this is if you intend to repair your car's transmission then you better know whether it's a manual, classic automatic, DCT or CVT.

Installing OSes nowadays requires acquired knowledge about several aspects of the hardware and OS requirements, namely BIOS or UEFI and its specific requirements (particularly when dealing with Windows or any dual- or multi-booting scenario involving Windows), partitioning types, partitions & file systems (intimately related to the previous point), the different boot processes in BIOS/Legacy and UEFI... And a large etecetera.

And yes, it also requires one to be humble enough to understand when experts say things as authoritatively as your first replies here, they probably know what they're talking about. All subsequent replies as well.  



> The term "tone" I think can be used in the context of your response (...) sounded condescending. It's sometimes  hard to judge someone's intentions only through written word so if I  misjudged you, It wasn't intentional.

No, the tone I was referring to was the general tone of the replies you got here even before my first post here, particularly the option of not responding directly to what you though was the solution but instead explaining why it wasn't, why issue A and issue B are unrelated and especially the why providing you with a "solution" for A wouldn't have any weight on B. Please go back and read the sequence. I think now you will understand it better if you read my previous long comment.
And you're partially correct - no misjudgment - as I am at times condescending. I admit I have a problem with certain attitudes. I admit I have a problem with users not wanting to learn and thinking they know best - just answer my g'damn question that I now is the solution, I don't care about your alternative -. This always ends badly. If I misjudged your attitude, it wasn't intentional, and please fell free to post other questions if you're willing to listen to others. 
The good luck with Windows part, however, it's not condescending. Everybody needs some luck with Windows and all the malware in the wild - it wasn't personal - and everybody using Windows should be aware of that.

Again, good luck in your endeavors.

---

