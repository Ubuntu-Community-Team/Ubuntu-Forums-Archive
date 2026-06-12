---
title: "How to resize Hard drive in Virtualbox"
date: 2007-12-08
forum: Virtualisation
---

### Post by oneadvent on 2007-12-08
How do I make my virtual Hard disk bigger?

It is very new, but I do not want to reinstall because then I might have to call microsoft for activation, and that is annoying.

So back to my question. I did try to use gparted like other threads have suggested, but it doesn't allow me to make it any bigger.

Thanks,

Joshua

---

### Post by los santos on 2008-03-05
**use these instructions at your own risk**, they worked for me but you have to be careful when working with partitions. i recommend **backing up all your data before you start**.

start by making a new drive through the virtualbox drive manager. i chose to make mine 30GB. set this drive to be the primary slave for the system you want to upgrade. 

next download the clonezilla livecd iso from sourceforge [http://clonezilla.sourceforge.net/download/sourceforge/](http://clonezilla.sourceforge.net/download/sourceforge/)

and the gparted livecd
[http://sourceforge.net/projects/gparted/](http://sourceforge.net/projects/gparted/)
note: i could not get the latest version (3.4.11) to boot in my virtualbox. it hung during boot at mounting usbfs. i tried version 3.3.7 and this version booted correctly.

once you have these iso files, set your virtual machine to boot from the clonezilla iso. boot it (default options should be fine) and choose a disk to disk clone. set your old virtual drive (probably /dev/hda) as the source and your newly created virtual drive (probably /dev/hdb) as the target. for the options, i think i chose do NOT install grub bootloader and left everything else at the default. let it make a copy of your disk (can take a long time) then poweroff your virtual machine.

now you have (hopefully) an identical copy of your virtual machine but on a bigger disk. to let your guest operating system see the new drive space, you have to expand both the partition table and the file system. 

at this point you could release your old virtual drive and set your newer, bigger virtual drive as the primary hard disk. set your virtual machine to boot from the gparted iso and run ```
cfdisk
``` once its booted up. if you have your new virtual disk set as the primary, cfdisk should automatically load its partition table. you should see something like /dev/hda1 with a size given by whatever your original virtual drive was, and then free space. go ahead and delete the partition, then create a new partition which takes up the entire available space. set this new partition to be bootable and change its type to ntfs (07 in cfdisk).

at this point, you should reboot to update the partition table changes. now the only thing left to do is expand the ntfs filesystem. this can be done with ntfsresize (program on the gparted live iso). to be safe, boot into windows now and run chkdsk /f in the terminal and then reboot into windows again. this will force windows to check its ntfs filesystem so there should be no errors that ntfsresize will complain about. after this is done, boot into gparted again. run ```
ntfsresize -i /dev/hda1
``` (or whatever your drive letter is). ntfsresize will tell you the size in MB of your virtual drive, so to be safe, resize to 1 MB less than this size. 

for my drive, ntfsresize told me it was 32113MB so I chose to resize to 32112MB. to do this run ```
ntfsresize --no-action --size 32112M /dev/hda1
```

if this command returns without errors, take out the --no-action flag and run it for real. once this is done reboot into windows. it will run a checkdisk again, reboot, and now you should see your bigger drive available.

---

### Post by xbYdx on 2008-03-20
Thanks for this howto.  Using the newest version of clonezilla (**clonezilla-live-1.0.9-19.iso**) you might not have to use gparted to resize the partition.  Clonezilla had the option: 
[INDENT]**-e "Resize the filesystem to fit partition size in target partition."**[/INDENT]
which I selected and it tried to resize the copied partition to the size of the new disk.  It failed for me because the FAT32 partition I was using had windows log files that weren't the expected size.

**Some other notes:**
[LIST]
[*]**Use space bar to select the target and destination disks.** An asterisk will appear.  Pressing enter when the desired drive is highlighted just exits the process, and gives you the option to start over, powerdown, restart, etc.

[*]**Unselect option -g-auto** (write grub).  This is in the same menu as -e above.

[*]After starting the copy it will give a couple of warnings about all data being lost on the destination drive.

[*]**Select yes when it asks "Do you want to clone the bootloader?"**

[*]On a 7200 rpm disk it copied at a rate of ~300 MB / minute.
[/LIST]

---

### Post by paraplegicpanda on 2008-04-29
I just confirmed that the "Resize the filesystem to fit partition size in target partition." option with Clonezilla does the trick. I ran clonezilla on my 10Gb vdi and cloned it to a 30Gb vdi using this option with no problem. Worked very well.

---

### Post by kvasanthkumar on 2008-11-19
paraplegicpanda,

I tried the same but, it only transfers to target partition with same size of the source partition.

Could you please provide me the procedure you followed to Clone with resized partition size ?

Thanks

---

### Post by kvasanthkumar on 2008-11-19
Hi,

Please ignore the request.
I used CloneZilla to copy the partition and GParted to resize, i got the free space as required.

---

### Post by motin on 2009-04-29
There is a great guide on the subject here: [http://www.my-guides.net/en/content/view/122/26/](http://www.my-guides.net/en/content/view/122/26/)

---

### Post by jet2230 on 2010-07-17
> **los santos said:**
> **use these instructions at your own risk**, they worked for me but you have to be careful when working with partitions. i recommend **backing up all your data before you start**.

..

i had made this fatal mistake of setting up a 8gig virtaul box partition for ubuntu 10.04 32bit (windows 7 64bit as host), primary reason was to fully equip that vm with the android dev kit, with all bells and whistles - had no idea the andoid dev kit would be so huge - well after installing everything i needed i was only left with about 80 mega bytes of free space :o

thanks for the cloning steps, now i have replaced the 8gb with a 30gb virtual hard drive :D

---

### Post by jacksonam on 2010-08-30
the steps:
1. start Virtual Box and log on windows.
2. download free partition utility at: [http://download.cnet.com/Partition-Assistant-Home-Edition/3000-2094_4-75118871.html](http://download.cnet.com/Partition-Assistant-Home-Edition/3000-2094_4-75118871.html)
3. use partition tool to extend your partition.
if you need to create, delete or format, read [how to partition a hard drive]("http://www.extend-partition.com/resource/how-to-partition-a-hard-drive.html").

---

### Post by rcragun on 2010-09-11
> **jacksonam said:**
> the steps:
1. start Virtual Box and log on windows.
2. download free partition utility at: [http://download.cnet.com/Partition-Assistant-Home-Edition/3000-2094_4-75118871.html](http://download.cnet.com/Partition-Assistant-Home-Edition/3000-2094_4-75118871.html)
3. use partition tool to extend your partition.
if you need to create, delete or format, read [how to partition a hard drive]("http://www.extend-partition.com/resource/how-to-partition-a-hard-drive.html").

The above suggestion by "jacksonam" doesn't work.  Just tried it.  Perhaps the professional edition has this functionality, but the home edition (which is free) doesn't see that there is additional space, so it can't expand your partition beyond the maximum specified when it was created.

---

### Post by Melon Bread on 2010-10-16
> **jacksonam said:**
> the steps:
1. start Virtual Box and log on windows.
2. download free partition utility at: [http://download.cnet.com/Partition-Assistant-Home-Edition/3000-2094_4-75118871.html](http://download.cnet.com/Partition-Assistant-Home-Edition/3000-2094_4-75118871.html)
3. use partition tool to extend your partition.
if you need to create, delete or format, read [how to partition a hard drive]("http://www.extend-partition.com/resource/how-to-partition-a-hard-drive.html").
It worked for me, thank you.

---

### Post by demonboy on 2010-11-17
> **jacksonam said:**
> the steps:
1. start Virtual Box and log on windows.
2. download free partition utility at: [http://download.cnet.com/Partition-Assistant-Home-Edition/3000-2094_4-75118871.html](http://download.cnet.com/Partition-Assistant-Home-Edition/3000-2094_4-75118871.html)
3. use partition tool to extend your partition.
if you need to create, delete or format, read [how to partition a hard drive]("http://www.extend-partition.com/resource/how-to-partition-a-hard-drive.html").

This doesn't make sense. If you download and install Partition Assistant within the Windows environment, then how does windows see anything outside of the virtual hard disk it was installed on?

If this works for other people then perhaps you could explain to the rest of us how this is possible. Are you saying this is installed on Ubuntu? If so then these instructions are a little unclear.

---

### Post by fisheater on 2011-03-06
Hi,

I was trying to expand my virtual harddrive and nearly went crazy with the complexity. Then I stumbled on this, it worked with a bit of syntax change. Use it at your own risk, but it makes the entire process much simpler.

[http://www.eggheadcafe.com/sample-code/Windows7/46634dd4-87aa-48c1-b5d4-d1a743aa4d8b/resize-an-existing-dynamic-virtualbox-vdi-hard-disk.aspx](http://www.eggheadcafe.com/sample-code/Windows7/46634dd4-87aa-48c1-b5d4-d1a743aa4d8b/resize-an-existing-dynamic-virtualbox-vdi-hard-disk.aspx)

By using the VBoxManage terminal command, it is simple.

VBoxManage clonehd --existing /home/goat/.VirtualBox/HardDisks/goatXP.vdi /home/goat/.VirtualBox/HardDisks/goatXP_20GB.vdi 

Happy expanding.

---

### Post by Welly Wu on 2011-03-17
I just wanted to add to Fisheater's post by writing that I had to create a new fixed capacity virtual disk within Sun/Oracle Virtualbox beforehand to running the VBoxManage clonehd --existing command. Otherwise, VBoxManage complains that there is no target virtual disk to do the disk clone. Later on, I followed the directions for expanding the size of the hard drive by booting off of the new and larger capacity virtual disk, running the Disk Management snap-in tool, and extending the partition to the maximum capacity. It worked.

---

### Post by andig on 2011-07-06
You must go to folder where is OldDisk.vdi .
30000 = 30GB
```
VBoxManage modifyhd OldDisk.vdi –-resize 30000
```
And it's done :).

---

### Post by Bungtung on 2011-07-16
jacksonam - great tip, worked a treat.

the trick is that i needed to copy the vdi to a new virtual hard-disk with the expanded size - then i used Partition Assistant Home Edition to resize the partition to take up the extra space in the new virtual hard-drive.

---

### Post by andig on 2011-07-16
> **Bungtung said:**
> jacksonam - great tip, worked a treat.

the trick is that i needed to copy the vdi to a new virtual hard-disk with the expanded size - then i used Partition Assistant Home Edition to resize the partition to take up the extra space in the new virtual hard-drive.

```
VBoxManage clonehd "DiskToClone.vdi" "ClonedDisk.vdi"
```

---

### Post by mbelos on 2011-10-31
> **andig said:**
> You must go to folder where is OldDisk.vdi .
30000 = 30GB
```
VBoxManage modifyhd OldDisk.vdi –-resize 30000
```
And it's done :).

This worked for me, then in my Windows guest OS, I went to Disk Management and expanded the existing volume.

Thanks andig!

---

### Post by HermanAB on 2011-11-03
Hmmm, maybe stop and think why you need a bigger disk.  If it is only for data, then enable a shared folder on the host and put your data there.

I prefer keeping my VMs small and keep all the data outside the VM.  It is more storage efficient that way.

---

### Post by adsbaer12 on 2011-12-14
> **andig said:**
> You must go to folder where is OldDisk.vdi .
30000 = 30GB
```
VBoxManage modifyhd OldDisk.vdi –-resize 30000
```And it's done :).

Worked like a charm in VirtualBox  4.1.6 r74713. Thx andig! O:)

in terminal:
```
VBoxManage modifyhd "/home/user/VirtualBox VMs/YourVBoxGuestHDD.vdi" --resize 30000

```Afterwards simply boot your VBox-guest from a Ubuntu Live CD and start gparted in order to add the new free space to the existing Windows partition.

---

### Post by Rock Storm on 2013-01-02
**[SIZE=2]Disclaimer[/SIZE]**

Fully tested on a host running Ubuntu 12.04 and VirtualBox 4.2.6, it should work properly for almost any other Linux distribution as long as VirtualBox version is 4.0.0 or over.

In my case I had a virtual machine with a 10Gb virtual hard disk attached to it, which happened to be too small for some stuff. So here is what I did to expand the hard disk without cloning to other disks or whatever.

**[SIZE=2]Down To Business[/SIZE]**

Open a terminal and type:
```
VBoxManage list hdds
```Every single hard disk of every virtual machine will be listed. Look for the one you're willing to enlarge and copy it's UUID or location including filename. Next thing will be typing:
```
VBoxManage modifyhd <filename>|<uuid> --resize xxxx
```Now where it says <filename>|<uuid> you should paste whichever, the UUID or the full path, you copied, and replace xxxx with the number of MB desired for the new hard disk. So my line looked like this:
```
VBoxManage modifyhd /home/user/VirtualBox\ VMs/VirtualDemo/VirtualDemo.vdi --resize 20480
```Note that, this way, you can expand the hard disk capacity but never shrink it.

If the above went OK, you'll notice your disk has actually earned some MB but you can't use them once inside the guest operating system. Well, a final step is needed, and that would be growing your partitions so they fill the entire new disk. This depends too much on which OS you are using and what software you like most to do this kind of things. I used "GParted Partition Editor" which, by the way, comes pre-installed in the latests Ubuntu LiveCDs. Meaning that if your host is currently Windows you can always use this LiveCD and modify partitions using GParted without even installing Linux.

Complete and much more detailed information can be found at:
[http://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvdi](http://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvdi)

If your host is windows or all the above explained didn't do, this might be of help:
[http://tips.kaali.co.uk/2012/03/16/expand-or-increase-the-size-of-virtual-box-vdi-dis/](http://tips.kaali.co.uk/2012/03/16/expand-or-increase-the-size-of-virtual-box-vdi-dis/)

---

### Post by howefield on 2013-01-02
Old thread closed.

---

