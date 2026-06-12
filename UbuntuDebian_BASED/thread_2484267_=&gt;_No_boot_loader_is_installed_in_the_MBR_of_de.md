---
title: "=&gt; No boot loader is installed in the MBR of /dev/nvme0n1."
date: 2023-02-21
forum: Ubuntu/Debian BASED
---

### Post by bgmarouene on 2023-02-21
[https://pastebin.ubuntu.com/p/fttr6CKh3k/](https://pastebin.ubuntu.com/p/fttr6CKh3k/)

I am using Lenovo Thinkpad L390 with Ubuntu 22 and Windows 11 installed in dual boot mode.

I was working on Ubuntu and suddenly the laptop crashed and I got that Gru command line.

Any help will be appreciated.

Thanks!

---

### Post by oldfred on 2023-02-21
That is not an error & just points out that you do not have the 40 year old BIOS boot loader as you have a newer UEFI system with UEFI boot using the ESP - efi system partition. You can see both Ubuntu & Microsoft folders with UEFI boot files in you nvme0n1p1.

Report is missing everything else as every other partition is shown as unknown.
Did a Windows update turn Windows fast start up back on? Then from Linux NTFS driver the NTFS partitions may not be shown.
But not seeing a Linux ext4 partition may mean file corruption.

If Windows boots check if fast start up is back on?

Can you mount nvme0n1p5 and run fsck since ext4?
To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown to your partition(s) edited to p5 if that is correct.
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/nvme0n1p5
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/nvme0n1p5

---

### Post by bgmarouene on 2023-02-21
Thanks for your response!

About Windows, it is starting fine yes. I checked there and[COLOR=#000000] fast start up is already on.[/COLOR]

[COLOR=#000000]For mounting nvme0n1p5 and running fsck since ext4, from where should I run the commands you asked to run ? Don't think from Gru command line the majority of the commands are not recognized.[/COLOR]

---

### Post by bgmarouene on 2023-02-21
Note that I used to get in the past few UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY errors sometimes and fixed them each time by running [FONT=var(--ff-mono)]fsck -fy /dev/[/FONT][COLOR=#000000]nvme0n1p5[/COLOR]

---

### Post by oldfred on 2023-02-21
Fast start up should be off in Windows if you want to see the NTFS partitions from Linux.

It sounds like it was telling you that you had some issues. It should not need fsck on every reboot.
Were you shutting down normally, not just powering off?

You may not want to check Smart Status. Windows does not always show issues until you have a total crash.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
In Disks alias gnome-disks you can click on icon in upper right corner and see Smart Status
[https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1](https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1)
If not Ubuntu but other flavor, you can install it.
sudo apt-get update -y
sudo apt-get install -y gnome-disk-utility
Smart Data 
[https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854](https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854)

---

### Post by bgmarouene on 2023-02-22
Sorry, but I am not able to launch ubuntu, then from where can I run the commands you asked to try ? Thanks.

---

### Post by ajgreeny on 2023-02-22
Run them from the live USB you probably used to install Ubuntu, making sure you get all device names/numbers correct as they might show differently from the USB system.

---

### Post by bgmarouene on 2023-02-22
Hi, I tried from the USB where where I installed Boot Repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) to investigate my issue, but it is displaying only the USB drive partitions and not the hard drive ones.

/dev/loop0 : 763.MiB
/dev/sda : 1.9 Gib
/dev/zram0 : 11.6 Gib

---

### Post by yancek on 2023-02-22
Does the USB you are using have an Ubuntu live system on it or is it just the iso file of boot repair?  If it has the full Ubuntu, you should be able to run fsck from there.  

> but it is displaying only the USB drive partitions and not the hard drive ones.  

You indicated in an earlier post that fast startup was "ON" and were told it needed to be "OFF".  Did you turn it off?  Linux systems won't mount and therefore will not show hibernated systems/partitions.  

>   was working on Ubuntu and suddenly the laptop crashed and I got that Gru command line.

Did you have the inconsistency errors prior to this crash?  As pointed out above, you definitely should not need to run fsck on every reboot so there is some other problem.

---

