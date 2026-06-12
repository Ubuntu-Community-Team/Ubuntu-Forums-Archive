---
title: "Can someone explain this error issue with Ubuntu 13.10 64bit"
date: 2013-12-08
forum: Virtualisation
---

### Post by electrohandyman501 on 2013-12-08
Ok, here's what I have. I have a Samsung Laptop Win7 64bit install host(2 of 4 processors 2G ram), have a guest install of Ubutnu 13.10 64bit Kernel 3.11.0-12-generic (per the uname-l listing).
I had software package updates available so I initiated the update thru the GUI software updater and it failed.
I then went command line thru terminal. apt-get update then apt-get uprade to initiate the install. The install went ok for the most part until......

I got a popup box asking for grub write permissions to /dev/sda. (my windows boot partition). I denied the writing as I have not shared the win 7 boot partition to any of my VMWare guests.

So can anyone explain or know why the grub updater would want to write to the raw sda boot disk it's not supposed to see? 
My VM is sized at 20Gb at /dev/sdb1 with system partition 2Gb at /dev/sdb2 and swap 2Gb at /dev/sdb5

The following was copied from the terminal screen during the upgrade. If you want to see more let me know.

```
Setting up grub-common (2.00-19ubuntu2.1) ...
Setting up grub2-common (2.00-19ubuntu2.1) ...
Setting up grub-pc-bin (2.00-19ubuntu2.1) ...
Setting up grub-pc (2.00-19ubuntu2.1) ...
/usr/sbin/grub-bios-setup: error: cannot write to `/dev/sda': Input/output error.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-12-generic
```

It's not earth shattering if I can't figure it out, as I'm only evaluating this version. But I was concerned that it wanted to write to the raw boot partition, when it's a virtual machine.

Thanks.

---

### Post by oldfred on 2013-12-09
I do not know how it is with a VM.
But grub normally installs to sda, so in a VM where does it install.

Then grub remembers where it installed originally and trys to reinstall there.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

I think if you unchoose everything then the default install is blank and it will not reinstall. Not sure if then updates to grub still work or not, or if it is just the boot loader install that is not done.

---

### Post by ian-weisser on 2013-12-09
/dev/sda is a common enough name.

You probably have two:
One on the VM host that refers to a real hard drive partition. 
Another on the VM guest that refers to the first hard drive *it* sees...meaning the VM file.

---

### Post by electrohandyman501 on 2013-12-09
> **ian-weisser said:**
> /dev/sda is a common enough name.

You probably have two:
One on the VM host that refers to a real hard drive partition. 
Another on the VM guest that refers to the first hard drive *it* sees...meaning the VM file.

My thinking along the partition line is that within the VM, it should only care about the VM file. Isn't that supposed to be the advantage of a VM.
I understand that the /dev/sda is a common identification, and normally I would think that within the VM environment the /dev/sda would be the "file" that the guest is contained within. After all the "file" is where it's installed.

What caught my attention was the pop up warning box that the guest OS wanted to write to the hard disk "outside" of the VM environment, I've not had an update try to do this before with any of my other linux VM guest os's. Nor did I have the question asked when I installed it.

Fred, I'll look at where the grub is located when I get some time, thanks for the listings.

Maybe I have something messed up with the VM setup or install. It's easy enough to wipe it out and re-create the VM. But I was curious if any others have had this experience.

---

### Post by ian-weisser on 2013-12-09
Apologies, upon reread I had missed the bit about the popup box. I would refuse, too.

---

### Post by electrohandyman501 on 2013-12-10
> **oldfred said:**
> I do not know how it is with a VM.
But grub normally installs to sda, so in a VM where does it install.

Then grub remembers where it installed originally and trys to reinstall there.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

I think if you unchoose everything then the default install is blank and it will not reinstall. Not sure if then updates to grub still work or not, or if it is just the boot loader install that is not done.

Ok, I think I found the key with my situation. In my VM setup I did have access enabled to partition sda5 (my windows D: drive).
When I ran the grub reconfigure I had an entry for the win 7 boot partition sda1 as well as the 2 VM sdb "partitions".
If I disabled the sda5 access to the VM environment, only my sdb virtual partitions were listed for the grub configure. 

I guess where I'm going here, I need to disable any sda disk access for any kernel updates so then there will be no attempt to write to the sda1 partition.

Thanks for the Info Fred. I'll call this one closed.

---

