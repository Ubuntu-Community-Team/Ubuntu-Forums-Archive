---
title: "vmware workstation problem"
date: 2008-03-18
forum: Virtualisation
---

### Post by sbrody88 on 2008-03-18
I'm having a weird problem with my workstation 6.  I'm trying to create a new virtual machine onto an external hard drive I have set up, and I'm getting the error "The current amount of free space on the hard disk (2.8 GB) is not enough to create the specified disk file: Windows.vmdk. Please choose a different location or specify a smaller disk size."  But the external hard drive has over 300 GB of free space left, and the VM I'm creating is only 40GB.  Any ideas?

---

### Post by gobbles414 on 2008-03-18
> **sbrody88 said:**
> I'm having a weird problem with my workstation 6.  I'm trying to create a new virtual machine onto an external hard drive I have set up, and I'm getting the error "The current amount of free space on the hard disk (2.8 GB) is not enough to create the specified disk file: Windows.vmdk. Please choose a different location or specify a smaller disk size."  But the external hard drive has over 300 GB of free space left, and the VM I'm creating is only 40GB.  Any ideas?

Are you using a static or expanding disk image. Some operating systems do not install well on expanding images. Does that help?

---

### Post by sbrody88 on 2008-03-18
I was doing a static disk image - allocating all the space for the VM up front.  When I do it expanding, it actually works, which makes sense since it thinks that my disk is too small for some reason, it can still install the small disk that will grow later, but it can't allocate all the memory for the VM at once.  Its important to me to have a high performance VM - I'd really like to get it to allocate all the memory at once.  Any help will be greatly appreciated.

---

### Post by gobbles414 on 2008-03-18
> **sbrody88 said:**
> I was doing a static disk image - allocating all the space for the VM up front.  When I do it expanding, it actually works, which makes sense since it thinks that my disk is too small for some reason, it can still install the small disk that will grow later, but it can't allocate all the memory for the VM at once.  Its important to me to have a high performance VM - I'd really like to get it to allocate all the memory at once.  Any help will be greatly appreciated.

What format is the external hard drive using (FAT, NTFS, EXT3)? Is journaling enabled?

---

### Post by sbrody88 on 2008-03-18
> **gobbles414 said:**
> What format is the external hard drive using (FAT, NTFS, EXT3)? Is journaling enabled?

It is NTFS, I have it mounted using the ntfs-3g read/write driver.  As for journaling, I'm not sure what that is... What is it, and how do I check whether or not its enabled?  Thanks for your help.

---

### Post by superprash2003 on 2008-03-18
i had a same problem.. it just wouldnt work with an NTFS drive.. i used the OS drive in the end.. /home/

---

### Post by gobbles414 on 2008-03-19
> **sbrody88 said:**
> It is NTFS, I have it mounted using the ntfs-3g read/write driver.  As for journaling, I'm not sure what that is... What is it, and how do I check whether or not its enabled?  Thanks for your help.

I've only had a chance to read a few threads regarding your issue. But some people do seem to have problems with VMWare in Linux on NTFS hard drives -- although most users seem not to have any difficulties. Try using EXT3. Or if you need to use this external hard drive with Windows-based PCs too, use FAT32.

Wikipedia defines journaling as, "...a file system that logs changes to a journal (usually a circular log in a dedicated area) before committing them to the main file system. Such file systems are less likely to become corrupted in the event of power failure or system crash." My understanding is that NTFS is a journaled file system.

Keep us informed on your progress, please.

---

### Post by sbrody88 on 2008-03-19
Well, I just tried to create an 8GB VM on my computers actual HDD, which is ext3, and I'm getting the same error.  So, it seems like this isn't actually a problem with my external hard drive after all, or a problem with ntfs.  But now I have no idea what actually is the problem.  I've made a VM on this machine before and it worked fine.  I made an 8GB windows VM, which is exactly what I just tried to do again, but this time it didn't work!  help.

---

### Post by gobbles414 on 2008-03-19
> **sbrody88 said:**
> Well, I just tried to create an 8GB VM on my computers actual HDD, which is ext3, and I'm getting the same error.  So, it seems like this isn't actually a problem with my external hard drive after all, or a problem with ntfs.  But now I have no idea what actually is the problem.  I've made a VM on this machine before and it worked fine.  I made an 8GB windows VM, which is exactly what I just tried to do again, but this time it didn't work!  help.

I'm out of ideas too. Are you opposed to trying VirtaulBox (click [here]("http://www.virtualbox.org/"))?

---

### Post by sbrody88 on 2008-03-21
I kind of don't want to do that, cause I already have some VMs set up in VMware and it would suck to have some running in VMWare and others in virtualbox.
I tried re-installing vmware, but that didn't help.  Can anyone help me figure this out?

---

### Post by obalonye on 2008-03-21
hi, i just just installed the Vmware workstation and i have created windows XP and i am getting this error trying to power on the virtual machine.. the error sayz

Unable to change virtual machine power state: Failed to connect to peer process.

plz any assistance?

---

### Post by ceesa on 2008-07-15
obalonye:

Had the same problem, VMs would not start and i received the message "Failed to connect to peer process". 

See [http://ubuntuforums.org/showthread.php?p=2990990](http://ubuntuforums.org/showthread.php?p=2990990)

Regards.

---

### Post by jake1017 on 2008-07-16
There is no reason to use Virtual Box. I have VMware Workstation and had the same problem when trying to create virtual disks on a partition. There is no solution that I know of but I simple and easy work around.
This is what you do:
Open a terminal session. Change the directory to your external Hard Drive (I suggest that you create a folder specifically for the virtual machine on your external hard drive). 

Enter this command in terminal: vmware-vdiskmanager -c -s 00.0GB -a ide -t 2 Name-of-Virtual-Machine.vmdk
 
Change 00.0GB to what you want the size of the virtual disk, in gigabytes, to be (make sure you keep the "GB" at the end). Put the name of the virtual machine where I have put "Name-of-Virtual-Machine".

Once it has finished creating the virtual disk open VMware Workstation and click "Create a new virtual machine". Choose custom instead of typical and follow instructions until you get to "Name the virtual machine". Change the location to the file directory that the virtual disk is in. Click next and follow instructions until you get to "Select a disk" choose "Use an existing virtual disk" and click next. Then click browse and go to where you created your virtual disk and select it. Follow the rest of the instructions and your done!:)

---

### Post by gcshum on 2008-07-17
It has happened to me as well. But I was installing PCLOS MiniMe2008 guest. The solution was using BusLogic rather than LsiLogic. I have no idea what they are. I just tried it and it worked. Give it a try and tell us if it works.

---

### Post by gcshum on 2008-07-17
By the way, you can't change LsiLogic to BusLogic when the virtual disk has been created. You have to do that before creating the disk.

---

