---
title: "Speed up/defrag Ubuntu 16.04 VM on windows 10 host using VMware"
date: 2019-11-06
forum: Virtualisation
---

### Post by torben545 on 2019-11-06
Hello everyone, 

my Ubuntu development VM has been slowing down considerably over the last months when it comes to booting time. It usually needs up to 5 minutes to get "started" and another 5 minutes to start up Pycharm, load the modules, a browser and so on. Compared to the VM I use for College, running Ubuntu 18.04, this VM takes a total of a minute to both boot the system and CodeBlocks, open a browser and so on.

On the VM I have been getting very close to full capacity of the allocated hard disk and then deleting like 70% of it again (the size is about 500GB). Background: I develop for a webapp that Upload possibly large files and then generates some more big stuff. So every process basically creates up to 500MB of files. After months of developing the disk obviously gets full and I delete most of it and now got into the habit of not letting it get to the place where I have like 2GB left...

I feel this might be a case where defragmentation could be useful on my VM system, even though lots of people say it's not that much needed on Linux systems. What I think supports this idea is that when loading up I have 100% disk activity on the disk the VM is on, at an access rate of less than 10MB/s. And the disk is easily capable of reading at well over 100MB/s. I know that since lots of files are loaded the speed won't reach that mark, however I still feel the gap is too large, especially since on my other VM it is over 5x faster. 

How do I defrag the guest on Ubuntu? I don't know much about partitions and defragging Linux systems, much less on a virtual system. 

Best and thanks a lot.

Computer I am using: OMEN by HP 15.6-inch Gaming Laptop, i5-8300H Processor, GeForce GTX 1050Ti 4GB, FHD IPS Thin Display, 12GB 2666MHz RAM, 1TB HDD & 128GB PCIE SSD, Windows 10 (15-dc0010nr, Black), Metal

---

### Post by johnarnold on 2019-11-06
Performance issues are nearly always to do with the way the VM is configured rather than the guest OS. Your first step should be to run the defrag utility in VMware.  I assume you are using workstation in which case it's VM -> settings -> select disk -> defrag. Also, it's important when using large disks to store them as a single file and to pre-allocate the data.

---

### Post by torben545 on 2019-11-06
Sorry, I forgot to mention I ran the defrag tool on VMWare that didn't help a lot. I have the VM in multiple files though. Could I bring them back into one and could that possibly help?

---

### Post by Skaperen on 2019-11-06
what type of filesystems are each partition formatted with?

---

### Post by johnarnold on 2019-11-06
Probably not worth the risk to try to consolidate those disk files now. Did you pre-allocate the space though? Also, have you got any snapshots on that VM? Snapshots seriously impact performance.

---

### Post by torben545 on 2019-11-06
The filesystem on the windows 10 host is NTFS, the guest is EXT4. I don't have snapshots of the VM, I just take manual copies to my external hard drive when the machine is shut down. How do you preallocate the space on the hard drive?

---

### Post by Skaperen on 2019-11-06
to pre-allocate space, split the hard drive up even more and make another partition.  this may cost a lot of effort with other partitions, so an external hard drive might be a big help.  then let the VM (and hence Win 10) use that partition or hard drive.  that should also be faster since there will be one less file system layer for all the I/O to go through.  hypothetical, that external hard drive can also be a dual-boot, if your BIOS can boot it.  i make all my data drives really bootable by also having Ubuntu on them as a runnable system.

---

### Post by TheFu on 2019-11-06
Tuning VMs has some general ideas that apply to all VM hypervisors.  Here's an old guide for VirtualBox, but it applies to VMware Player and Workstation and ESXi and ESX and Xen and KVM just the same:
[https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)

Spinning disks need to use preallocated storage.  For SSDs, it doesn't matter.

2G should be fine as a lower free space limit on /var/ for VMs.  Check out my link above, feel free to ask questions about any of the settings.

---

### Post by johnarnold on 2019-11-07
When you originally create the disk there is a check box to pre-allocate the space. To change it afterwards you need to use a utility called [COLOR=#3B444E][FONT=&amp]vmware-vdiskmanager. Here is an article that describes the process on Windows: [/FONT][/COLOR][https://www.techwalla.com/articles/how-to-change-a-vmware-disk-to-preallocated](https://www.techwalla.com/articles/how-to-change-a-vmware-disk-to-preallocated)

---

### Post by torben545 on 2019-11-07
Thanks for all the useful answers! I just shut down the VM and checked, the files take up around 300GB although the disk space used on the VM (in Ubuntu Filemanager) is less than 100GB. Would it be possible to reallocate/preallocate the files to only 250GB? I am pretty sure this is all I am going to need. Or should I reclaim unused space first? If I switch to pre-allocated storage, can I also switch into "one-file-mode" during the process? And would that make sense?

---

### Post by TheFu on 2019-11-07
Split the storage into multiple VMDK files.  The sparse vs fully-allocated happens at the VMDK file level.
Then you'd mount the other storage to somewhere specific.

The process is effectively  
old-sparse allocation ----> copy-into -----> New fully-preallocated allocation
I've never used an in-place modification tool.

If you are tight on local storage, just backup like you normally would to external storage, then delete the VM storage and recreate it choosing to fully preallocate it. Then restore the backup using your normal process.

BTW, I haven't used any VMware products since around 2011.  Workstation is an excellent desktop-on-desktop solution, if that is your need.

---

### Post by torben545 on 2019-11-20
Hey, took a bit to get back to you.. I have the new hard disk in the machine now, it is of size 200GB, and I installed one partition of size 200GB. Currently I use 96GB in the system. So how do I make this my main/boot partition (such that I can then remove the old, not preallocated drive after)? Since I did not get the machine to boot from a USB to use something like CloneZilla as described here [https://askubuntu.com/questions/741723/moving-entire-linux-installation-to-another-drive](https://askubuntu.com/questions/741723/moving-entire-linux-installation-to-another-drive) I wondered if shrinking the current main partition and then using DD for cloning as described here [https://serverfault.com/questions/4906/using-dd-for-disk-cloning](https://serverfault.com/questions/4906/using-dd-for-disk-cloning) is a viable option? Thanks!

---

