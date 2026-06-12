---
title: "Trouble configuring RAID when installing"
date: 2019-05-03
forum: Server Platforms
---

### Post by zogthegreat on 2019-05-03
Hi everyone!

I'm trying to install Ubuntu 18.04 on one of my computers and I'm having trouble with configuring soft RAID when installing. I am trying to follow the instruction found here:

[https://help.ubuntu.com/lts/serverguide/advanced-installation.html.en](https://help.ubuntu.com/lts/serverguide/advanced-installation.html.en)

"[COLOR=#333333][FONT=Ubuntu]**Partitioning**

[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][FONT=inherit]Follow the installation steps until you get to the [FONT=inherit]*Partition disks*[/FONT] step, then:[/FONT]
[FONT=inherit][FONT=inherit]
[LIST]
[*=left][FONT=inherit]Select [FONT=inherit]*Manual*[/FONT] as the partition method.[/FONT]
[*=left][FONT=inherit]Select the first hard drive, and agree to [FONT=inherit]*"Create a new empty partition table on this device?"*[/FONT].[/FONT]
[FONT=inherit]Repeat this step for each drive you wish to be part of the RAID array.[/FONT]
[*=left][FONT=inherit]Select the [FONT=inherit]*"FREE SPACE"*[/FONT] on the first drive then select [FONT=inherit]*"Create a new partition"*[/FONT].[/FONT]
[*=left][FONT=inherit]Next, select the [FONT=inherit]*Size*[/FONT] of the partition. This partition will be the [FONT=inherit]*swap*[/FONT] partition, and a general rule for swap size is twice that of RAM. Enter the partition size, then choose [FONT=inherit]*Primary*[/FONT], then [FONT=inherit]*Beginning*[/FONT].[/FONT]
[FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit]A swap partition size of twice the available RAM capacity may not always be desirable, especially on systems with large amounts of RAM. Calculating the swap partition size for servers is highly dependent on how the system is going to be used.[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[*=left][FONT=inherit]Select the [FONT=inherit]*"Use as:"*[/FONT] line at the top. By default this is [FONT=inherit]*"Ext4 journaling file system"*[/FONT], change that to [FONT=inherit]*"physical volume for RAID"*[/FONT] then [FONT=inherit]*"Done setting up partition"*[/FONT].[/FONT]
[*=left][FONT=inherit]For the [FONT=inherit]*/*[/FONT] partition once again select [FONT=inherit]*"Free Space"*[/FONT] on the first drive then [FONT=inherit]*"Create a new partition"*[/FONT].[/FONT]
[*=left][FONT=inherit]Use the rest of the free space on the drive and choose [FONT=inherit]*Continue*[/FONT], then [FONT=inherit]*Primary*[/FONT].[/FONT]
[*=left][FONT=inherit]As with the swap partition, select the [FONT=inherit]*"Use as:"*[/FONT] line at the top, changing it to [FONT=inherit]*"physical volume for RAID"*[/FONT]. Also select the[FONT=inherit]*"Bootable flag:"*[/FONT] line to change the value to [FONT=inherit]*"on"*[/FONT]. Then choose [FONT=inherit]*"Done setting up partition"*[/FONT].[/FONT]
[*=left][FONT=inherit]Repeat steps three through eight for the other disk and partitions."[/FONT]
[/LIST]
[/FONT]
[/FONT]
[/FONT]
[/FONT][/COLOR]

However, when I try to do this, I can't find the section "physical volume for RAID". 

[IMG]http://ohsmeg.com/bill/projects/computers/stuff/RAID_1.png[/IMG]

My setup is as follows:

Supermicro X8DTT-F motherboard

1 x 500gb SATA as OS drive
3 X 2tb SATA for RAID 0 volume

Can someone explain to my where I'm messing up? 

Thanks!

zog

---

### Post by oldfred on 2019-05-04
Moved to the server sub-forum where those that may know RAID better could help.

If separate OS drive, you should just do a standard install to that and then set up RAID as data partition(s).

Do not know RAID, but have seen many posts where RAID 0 not recommended.
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by zogthegreat on 2019-05-04
Hi oldfred,

Thanks for the reply. What I ended up doing is mounting the array in a subfolder in my /home directory. Ugly, but it works for my needs.

Yes, I understand the risk of RAID 0. What I'm using the machine for is compiling photogrammetry images for 3D printing, so I need the fast I/O verse reliability. All of the original pic's are backed up, so if a drive fails, I just lose the current work.

Thanks again!

zog

---

### Post by oldfred on 2019-05-04
For fast, you might want to consider NVMe drives.
But that probably is a new system to have the correct hardware support, both physical & software.

---

