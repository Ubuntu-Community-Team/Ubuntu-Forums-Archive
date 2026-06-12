---
title: "Large Raid Setup"
date: 2008-06-18
forum: Server Platforms
---

### Post by shazard1 on 2008-06-18
I am in the process of setting up a large raid array to act as a photography sever. I am using a Adaptec Raid card (31605) in a raid 6 array with 16 1 TB drives. Any suggestion as to how to setup Ubuntu Sever Edition on the array. I had tried to install on the array itself, but it will not boot. All I can get is a blinking white dash. I installed it on a drive outside of the array and it will install and boot but I have trouble accessing the array. Also when I try to format the array it will only format 750 gb instead of the total 12 TB.

---

### Post by smileypaul on 2008-06-18
You will need a separate single drive for the OS.

and for breaking the 2tb limit, you'll need to google GPT .. basically set the disk as GPT type, then you should be able to format to your 12Tb.

ps: thats a lot of TeraBytes! i run an offsite DataStorageCompany, and have still not come close to that! im at 4Tb.. i guess business needs to pick up :)

Bes tof luck.

---

### Post by rickyjones on 2008-06-18
> **smileypaul said:**
> You will need a separate single drive for the OS.

and for breaking the 2tb limit, you'll need to google GPT .. basically set the disk as GPT type, then you should be able to format to your 12Tb.

ps: thats a lot of TeraBytes! i run an offsite DataStorageCompany, and have still not come close to that! im at 4Tb.. i guess business needs to pick up :)

Bes tof luck.

I just want to add that I would actually install on two separate drives in a RAID1 array. That is proven to work.

Thanks,
Richard

---

### Post by shazard1 on 2008-06-18
Thank you both for the quick reply I'll give it a try
Steven

---

### Post by olivero on 2008-06-18
Hi Shazard,

in order to boot, Linux needs a 'simple' drive that is marked with a boot-flag and is low-level accessible through the BIOS. Whenever the computer starts, the first code being executed is prehistoric and knows nothing about raids. Compare it to trying to do advanced calculus with only a brain stem from the Jurassic to work with.

For booting, I've set up a simple raid 1 with two drives. You can do the setup with the ubuntu installer on any two small drives. Important: It has to be raid 1 (Mirror only) because any other raid will de-sequentialize the data and render it useless for the BIOS in order to boot the linux kernel. 

Take a look at this post, it covers the basics to get your Linux system onto Raid1: [http://www.howtoforge.com/software-raid1-grub-boot-debian-etchd](http://www.howtoforge.com/software-raid1-grub-boot-debian-etchd) 

Now for your real storage, you've got two options:

1) Linux supports your controller: 

```
- Configure your raid using the controller BIOS/tools
- Include the (proprietary) drivers into your kernel (may require modprobe and rebuilding your boot image. Check the manual of your controller)
- Reboot and mount the raid 

```

2) Linux Software Raid (md)

Boot your machine and make sure, all disk devices are visible:

```

root@Kaneda:/# ls /dev/sd*
/dev/sda   /dev/sdb  /dev/sdc   /dev/sdd  /dev/sde ... /dev/sdk  

```

ls should give you 12 sdx devices... if it doesn't, linux doesn't support your card and you need a proper driver.

The next step is to build the array (Assuming level 5 on 12 disks, no spares):
```

mdadm --create -l 5 -n 12 /dev/md2 /dev/sdc [...] /dev/sdm

```

Substitute the [...] above with the list of all your 12 devices. It must match the number given after the -n, or the array won't start.

Afterwards check, if the raid is up and running. Running cat /proc/mdstat should give you something like this (Assuming /dev/md0 and /dev/md1 are your boot + SWAP devices):

```
root@Kaneda:/# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid5 sdc[0] sdd[1] sde[2] sdf[3] [...] sdm[12]
      12615112576 blocks super 0.91 level 5, 64k chunk, algorithm 2 [4/4] [UUUUUUUUUUUU]
      [=====>...............]  reshape = 29.5% (340841344/11307556288) finish=2703.3min speed=1333K/sec
      
md1 : active raid1 sda2[0] sdb2[2]
      1003968 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      4008064 blocks [2/2] [UU]
      
unused devices: <none>

```

Make a filesystem on the raid array: mkfs -t ext3 /dev/md2

Mount the array: mount /dev/md2 /mnt (Any empty directory)

In any case the file system and kernel must support disk sizes > 4GB. I don't know if there are limits in ext3fs and if you have to bind any additional modules into your kernel. Maybe somebody else can help!

I hope this helps.
Oliver

---

### Post by fjgaude on 2008-06-18
The default ext3 can handle files to 2TeraBytes, disks to 8TeraBytes, if memory serves. You can google to be sure.

---

### Post by tubezninja on 2008-06-18
Max volume size on ext3 is up to 32TB, with a max individual file size of 2TB.

Edit: Make that 16TB.

---

### Post by fjgaude on 2008-06-18
This 32TB, is that with 16KB blocks instead of the default 4KB?

---

### Post by shazard1 on 2008-06-19
The proprietary drivers are rpms is this an issue?

---

### Post by fjgaude on 2008-06-19
It is if they don't convert with **alien** to deb. Else you will have to get the source code and compile.

---

