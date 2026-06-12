---
title: "Can't install Raring as the installation hangs on the partitioner"
date: 2012-12-23
forum: Ubuntu Development Version
---

### Post by sonnet on 2012-12-23
I tried to install Kubuntu 13.04 with the images from the last 3 days (including today). The problem is that the installation hangs on the partitioner: as soon as a click continue (on the initial screen where you can select whether include or not proprietary software or download updates) the system hangs (it never gets to the next screen).

So I tried Ubuntu Server 13.04 and tried a cli.
I get the same problem: after the first selections, when it's supposed to load the partitioner, the system hands (it never gets there).

I have 3 hard disks (1 ssd and 2 traditional ones).
I have a cpu intel i5- sandy bridge and a gtx 480 with 32gb of ddr3.
The system works fine while installing xubuntu 12.10 or ubuntu server 12.04.1

Any ideas/suggestions about what could be the isue?

---

### Post by sgage on 2012-12-23
> **sonnet said:**
> I tried to install Kubuntu 13.04 with the images from the last 3 days (including today). The problem is that the installation hangs on the partitioner: as soon as a click continue (on the initial screen where you can select whether include or not proprietary software or download updates) the system hangs (it never gets to the next screen).

So I tried Ubuntu Server 13.04 and tried a cli.
I get the same problem: after the first selections, when it's supposed to load the partitioner, the system hands (it never gets there).

I have 3 hard disks (1 ssd and 2 traditional ones).
I have a cpu intel i5- sandy bridge and a gtx 480 with 32gb of ddr3.
The system works fine while installing xubuntu 12.10 or ubuntu server 12.04.1

Any ideas/suggestions about what could be the isue?

This seems to happen from time to time. Occasionally, I've had success booting to "Try Ubuntu" and then running the installer from the icon on the desktop (not the one in the launcher). That's how I did this install, in fact :KS

---

### Post by rrnbtter on 2012-12-23
Greetings,
Install from "Try Ubuntu". +1 Also, It may help to disconnect every thing that you can disconnect until it is installed. You may also want to partition the drive the way you want it prior to running the installation. You can then choose to use the partitions and flag them the way you want. Worth a try, always works for me. Or not!

---

### Post by sonnet on 2012-12-23
Ok guys, I'll try it out in one hour and report back

---

### Post by grahammechanical on 2012-12-23
Something like this was happening when the first ISO images of Raring were released. At that time you could get to the partitioner page but no further. It was as if the partitioner was not on the disk. It was but there was an error in a script file that was supposed to call to next stage.

This could be a bug.

[http://ubuntuforums.org/showthread.php?t=2081344]("http://ubuntuforums.org/showthread.php?t=2081344")

Regards.

---

### Post by sonnet on 2012-12-23
Ok i tried from the live session (of Kubuntu: I tried the Alpha 1 images as also the latest daily build), as suggested, but I still have the same issue.

---

### Post by Chazall1 on 2012-12-23
I had no luck at all on several attempts. Here is what I did, Installed 12.10, changed the sources list to raring, and dist-upgrade, and here I am.

---

### Post by sonnet on 2012-12-23
> **Chazall1 said:**
> I had no luck at all on several attempts. Here is what I did, Installed 12.10, changed the sources list to raring, and dist-upgrade, and here I am.
Would it work if I do the same , but with a 12.04 cli installation (changing the sources to raring as you did?) ?

---

### Post by cariboo on 2012-12-23
> **sonnet said:**
> Would it work if I do the same , but with a 12.04 cli installation (changing the sources to raring as you did?) ?

No as explained in the thread you started, you first need to upgrade to Quantal first, before upgrading to Raring.

---

### Post by Rukiri on 2012-12-24
The installer seems broken, the best way to try raring at this point would be to just upgrade from a fresh 12.10 install.  This is what I plan on doing as I've wasted to much time and went through various hardware configs it is the installer that is broken.  

However, I did give 32GB of memory and 4GB of video to raring and I must say once you get it up it is snappy and really doesn't have a lot of issues as 12.10 did during beta.

---

### Post by P-I H on 2013-01-22
My 13.04 test system is working fine and I decided to test 13.04 on my main system. There are two SSD disks and I can keep the 12.10 installation unchanged. 
I downloaded today and used the dd command to copy the installation files to an USB flash drive.
The USB drive booted OK and the "Live environment" worked fine. However the installation hangs on the partitioner. I mounted the disks, started the installation and got the message to unmount the disks. I unmounted and tried to install again, but there was no difference.

There seems to be a bug report on this problem
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1080701)

---

### Post by jerrylamos on 2013-01-23
On 23 January amd64 ubiquity partitioner says it can't install to a partition outside the disk.  

Nonsense.  An existing partition is selected, which had a previous raring running in it.  No change in size of partition is being asked.

Launchpad bug 1100466.  

This bug has been around since at least 16 January, that's a week or more.

Today apport said there was an existing bug 1103213 but could not display it.  Must be marked private.

---

### Post by redcylon on 2013-02-09
Facing the same problem as others even up to latest build as of February 8th. Having machines with 4 physical hard disk installed. 

Take out 3 of the disk, leaving one for boot. Run the bootdisk and was able to install.

---

### Post by phibxr on 2013-02-09
Yes, I had to remove my SSD-disk to be able to progress with the installation as well.

I've added my partition layout to the launchpad bug. Installing 12.10 or other distributions worked fine, but 13.04 would hang while trying to start the partitioning tool. :(

---

### Post by ronparent on 2013-02-12
I have experience the same problem since early in the testing cycle. I searched through a bug report for this problem and found a suggested work-around from one of the recent posts that suggested turning off all the swaps (ie **sudo swapoff -a**). That did the trick for me ( on the third try) and the install to an ssd proceeded flawlessly. I do hope that the developers get to the root of the problem - but meanwhile I am a happy camper. 13.04 has been otherwise amazing (including on a fakeRAID 0).

---

### Post by cole.mickens on 2013-02-17
I reported this bug, or a related one: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1120938](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1120938)

Log posted there  as well. Installer hangs unless I disconnect my BTRFS drives that are in  RAID10.

---

### Post by Teunis on 2013-03-17
I just experienced the same trying to install on a Thinkpad with a second HD in a caddy.
After removing the caddy the install went OK.

---

### Post by cole.mickens on 2013-03-17
This is a very frustrating bug. I've asked repeatedly for help debugging it, I'm willing to sit there with GDB and ubiquity on my machine if someone would help me know what to look for.

---

### Post by deri on 2013-03-17
I have had issue too, but don't remember the version I had the problem with. Not always seeing the partioning. It was long before this 1st beta. I have been using 13.04 raring for some time already. Seems very stable and fast (kubuntu).

---

### Post by piriton on 2013-04-07
I've also had problems installing ubuntu 13.04 beta 2 which hangs on the partition editor.  I installed from the DVD.

I was able to get around this by removing the 2 files.
[COLOR=#000000][FONT=sans-serif]
sudo rm -rf /lib/partman/automatically_partition/15reuse/ /lib/partman/automatically_partition/25replace/[/FONT][/COLOR]

I now have a strange issue that i've not yet seen posted.

My partitions are listed twice during the "Prepare partitions" screen.

/dev/mapper/vg_name-lv-home
/dev/apper/vg_name-lv-home ext3 ext4 20000MB
..
..

I am unable to remove the first partition.

Any suggestions what I can try next ?

---

### Post by Kladiator on 2013-04-07
I have the same issue.

I tried to install first Ubuntu Gnome 13.04 and then Ubuntu Raring, from DVD and USB with no luck.

I had not seen this thread so, just to be sure, I installed on a free partition (my main OS is and will remain 12.04) Voyager 12.10,
which is based on Xubuntu and everything worked flawlessly.

Mine is not a complicated setup: only 2 hard disks and no SSD, Raid or whatever.

---

### Post by carolinason on 2013-04-22
I have this issue and have somewhat a simple work around, it works for whatever flavor of (K)(X)(G)ubuntu i happen to install. i like this method since i do not want to delete any partitions. also if you have to resize any parts before this method do that in a partition manager program before hand.

use the try ubuntu without installing option to get a live desktop. 

open a terminal window and in that terminal window  i make temporary mount points using mkdir and then mount them using mount or ntfs-3g depending on the partition's filesystem type in my case **NTFS** and **ext4**. this somehow pleases the partitioner so it will run. I have a dual boot, so i also mount windows system partitions. i then mount my 2 ext4 data partitions and one more ntfs partition. **i do not mount the / or /boot partition** i am going to use for this target installation. if you use a different file system than ext4 then use that FS in the mount command.

> 
:~$ sudo mkdir /path_to_a_temp_mount_for_non-target_linux_partition
:~$ sudo mkdir /path_to_a_temp_mount_for_windows_partition
:~$ sudo mount -t ext4 /dev/sdx# /path_to_a_temp_mount_for_non-target_linux_partition
:~$ sudo ntf3-3g /dev/sdy# /path_to_a_temp_mount_for_windows_partition
:~$ sudo swapoff -a


where x and y are the letter part of the partition IDs and # is the number part of the partID. like /dev/sda2, (just an example) a good tool to see **your** parts is to use the *lsblk* command.

I then start the installer. 

when the partitioner starts (where it had done nothing but spin my cursor before) i get a warning that the there are mounted partitions and would i like the installer to unmount them for me, since i they cannot be resized. i say **No**. but i then use the umount command to manually unmount the partitions in the same terminal i created them in, so they may edited in the partitioner.
> 
:~$ sudo umount /path_to_a_temp_mount_for_linux_partition
:~$ sudo umount /path_to_a_temp_mount_for_windows_partition


i then do a manual layout in the installer's partitioner and enter in the mount points for my file system table. swap is automatically recognized. all is straight forward after that. 

**enjoy 13.04!**

---

### Post by mrfelker on 2013-04-22
I had to do the following t get past the partitioner bug.
5  (3 physical disks)

2)  Install Ubuntu 12.04 LTS Alternate install.  Last Alternate install (terrible idea - lazy devs I guess)

3)  Upgrade to 12.10

4) Upgrade to 13.04.

This works fine but is tiresome.

---

### Post by FatAngus on 2013-04-22
I had to remove my 12.04 partitions and then create them during the Ubuntu 13.04 installation.

---

### Post by jallain on 2013-04-23
I've found that I too experience this issue on my fairly new HP Pavilion. What is interesting is that it installs just fine in a virtualbox. No problems at all. The issue seems to be hardware dependent.

---

### Post by jallain on 2013-04-24
I don't know if this is a work-around but it worked for me. I booted Ubuntu Gnome and selected "install" from the boot menu. I got to the part where it would not bring up the partitioner and quit the installation. After the system came all the way up I slected the installer once again. This time it went to the partitioner and I was able to install successfully.

---

### Post by Waddle on 2013-04-24
I just deleted all my partitions with Gparted in Live mode, then create partion with ext3 or ext4. Always works for me.

---

