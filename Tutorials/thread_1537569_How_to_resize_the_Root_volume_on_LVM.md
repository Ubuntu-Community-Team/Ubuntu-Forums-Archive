---
title: "How to resize the Root volume on LVM"
date: 2010-07-23
forum: Tutorials
---

### Post by wililupy on 2010-07-23
[FONT="Arial"]LVM is a great utility for being able to resize volumes on the fly. However, resizing the root (/) volume is tricky since you need to unmount the volume to do file system checks, and that is impossible if you are using it. I wrote this because I could not find a way to do it anywhere else, so I studied and figured it out on my own and figure others out there may want to do this.
My reason for this was because I needed more space in my /home directories, and my root directory was way to large for what I was using it for. I made it 30GB in size, and was only using 6GB and it was not going to grow any more. I decided to shrink the root file system from 30GB to 15GB and give the other 15GB to /home. This is how I did it.[/FONT]

The best way to do it is with the Ubuntu Live CD for Alternate Install. It has the LVM applications already to go.

[FONT="Arial"]1.      Reboot the computer with the CD in and boot off of CD.
2.	Select Rescue a Broken System. When it gets to the point of asking you to mount a file system, tell it not to mount any file system and run from the install root.
3.	From the command line, type [/FONT][FONT="Courier New"]lvmdiskscan[/FONT]
[FONT="Arial"]4.	This will show you all the disks. You will see your root volume. For these purposes, it is called /dev/VolGrp000/root.
5.	Run[/FONT][FONT="Courier New"] e2fsck -f /dev/VolGrp000/root[/FONT]
[FONT="Arial"]6.	After that completes, run [/FONT][FONT="Courier New"]resize2fs /dev/VolGrp000/root 3932160[/FONT]
[FONT="Arial"]I went to [http://www.unitconversion.org/unit_converter/data-storage.html ]("http://www.unitconversion.org/unit_converter/data-storage.html")to convert 15Gb to Blocks. Make sure you use Gb and not GB. Also, do not shrink your root filesystem smaller than what it being used. Make sure you know how much is being used and allow some room for growth. This takes a while to run.
7.	Once complete you can mount the volume and verify that it did shrink by running[/FONT] [FONT="Courier New"]mount /dev/VolGrp000/root /mnt [/FONT][FONT="Arial"]and then run [/FONT][FONT="Courier New"]df[/FONT] [FONT="Arial"]and you will see the new size. After this, unmount the volume with [/FONT][FONT="Courier New"]umount /mnt[/FONT]
[FONT="Arial"]8.	Now we can put the rest of the space back into the LV pool. Run[/FONT]
[FONT="Courier New"]lvreduce -L 15G /dev/VolGrp000/root[/FONT]
[FONT="Arial"]Word of caution, don't shrink it smaller then what you resize2fs it otherwise you will really break your system. This will put the space back into a Spare status and you can use it as you wish.
9.	Now, you can move the free 15GB to /home logical volume.[/FONT]
	[FONT="Courier New"]lvextend -L+15G /dev/VolGrp000/home[/FONT]
[FONT="Arial"]10.	Now you have to resize the filesystem to match the size of the logical volume[/FONT]
[FONT="Courier New"]resize2fs /dev/VolGrp000/home[/FONT]
[FONT="Arial"]11.	Reboot your PC and you are done.

I hope this helps anyone.:D[/FONT]

---

### Post by Hammi on 2011-08-31
Thanks for this tutorial. It did indeed help me. I had, however, to tweak a few steps which worked differently for me:

[LIST=1]
[*]Boot the Ubuntu Live CD (I had to install LVM2 with apt-get install lvm2, as I did not use an alternative install disk)
[*]I ran pvscan to scan the physical volumes (lvmdiskscan didn't work for me).
[*]Then I ran lvscan to scan for logical volumes. I then could see the root - let's stick to /dev/VolGrp000/root for this purpose.
[*]set active: vgchange -ay
[*]e2fsck -f /dev/VolGrp000/root
[*]shrink ext4: resize2fs -p /dev/VolGrp000/root 10G (no need to calculate blocks, just specify the size in gig)
[*]shrink logical volume: lvresize /dev/VolGrp000/root --size 10G
[/LIST]
At this point, I continued differently, as I had a different goal: I wanted to do was shrink the entire LVM medium (a  kvm/qemu raw disk image), not just "swap space" between two volumes. How I continued:
[LIST=1]
[*]pvresize will not yet work, if you have another logical volume (e.g. swap) sitting at the end of the physical volume. (pvresize manpage: "*pvresize   will  refuse  to shrink PhysicalVolume if it has allocated extents  after where its new end would be. In the future, it should relocate  these   elsewhere in the volume group if there is sufficient free space,  like pvmove does.*") We thus have to delete and recreate logical volumes sitting in the physical volume:
[*]Show volumes: lvs
Let's assume there is "swap_1" in VolGrp000, shown with a size of 884m.
[*]delete volume: lvremove /dev/VolGrp000/swap_1
[*]recreate volume: lvcreate --size 884M --name swap_1 VolGrp000
[*]If it was indeed swap, make it swap again: mkswap /dev/VolGrp000/swap_1
[*]resize physical volume to new size (11G) (finally!): pvresize --setphysicalvolumesize 11G /dev/vda5 (replace vda5 with whatever your physical volume is)
[/LIST]
You now can resize the partition or image file, depending on your setup. For me it was an image file, so I did:

[LIST=1]
[*]On the host machine, mounted the shrunk image as a loopback device: losetup -fv /path/to/image.raw
[*]show layout: fdisk -cul /dev/loop0 (assuming that the image was mounted as /dev/loop0)
[*]Note blocksize (512 Bytes for me), the start of the last device, and the number of blocks of the last device.
[*]Copy the needed blocks to a new image file: dd if=/path/to/image.raw of=/path/to/new_image.raw bs=<your_blocksize> count=<start_of_last_device+number_of_blocks_on_last_device>
[/LIST]
I hope this helps anybody.

---

### Post by jibcut on 2012-11-24
Since I can't make a new thread (new user) I thought I could put this related information here

Easy way to resize root

My situation was a little different:

- Hadn't used ubuntu in a while - this was on 11.04
-  This stemmed from update manager "Not enough free disk space" message,  so I needed to increase the size of my root folder, but it should be  just as easy to resize it in the other direction too
- This will also work for an encrypted system (I had installed ubuntu with the luks encryption)
- This is simply if you have enough space on your 'logical volume',  otherwise you have to create that extra space (using gparted to move  your whole drive around or using another partition or hard drive for  extra space) - see *** below
- I'm  writing instructions for a novice like myself


- In a nutshell - simply create some space, then a new partition (ext 4, in  my case) with gparted, then use 'system-config-lvm' gui to add that  space to the root partition. If you didn't encrypt your drive, this sentence above is as simple as it gets and a lot of the info below can be skipped.

>Would be a good idea to check your 'logical volume' names
     > sudo lvdisplay

>You should see the root, home, and  swap logical volumes and their  respective sizes; this will help determine which partition you have to  edit. I hoped you named them something similar like "vg_root",  "vg_home", etc., so you can determine which is which. Your home folder  should be larger than the others and you can load the 'Disk Utility' to  help determine which section you will edit in gparted.

>For  people with encryption, in disk utility,  you should see the 'extended'  section that has the two sub-partitions (I believe these correspond to  your Home folder and where the boot stuff is saved).

>Burn gparted to dvd and load that (you can find instructions for this elsewhere)

>Once  you have gparted open you should see all the partitions on your  hardrive, and it should look similar to what was seen with 'Disk  Utility'. Make sure you edit one of partitions that is already in the  'logical volume' (ones under the extended section). I believe it's  possible to take another drive, or unallocated space that isn't part of  the logical volume, but it's more complicated

Actually - moving your whole hard drive around isn't that hard - it just might take a long time depending on how big your hard drive is. (you just resize all the sections until you can add some space to the 'extended' drive that was created for the encryption.

***see here if interested:  [http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/))

>I didn't want to change the size of my encrypted home folder (I think that might be a bad idea anyway) - so I  made the boot(?) folder smaller since it had plenty of space  (it shows  you how much free space is available). After you click to resize it you  have to apply the changes.

>Now you have to click on that unused space you created and create a  new partition with it - this can then later be added to to the root  partition (I made mine ext 4 since that is what my root partition was)

>go back into ubuntu and install  'system-config-lvm' from the synaptic package manager (when installed  its called Logical Volume Management)

> Once installed, open it and on the left side you will see 'uninitialized entities'

>Find  the space you just created earlier - It should be the sda drive with the  highest number (double check if you have to, the size should be a dead  give away too)

>You initialize it, then add it the volume group

>go to root (or whatever you named it), under the 'logical view' section and click 'edit properties'

>Here  you can change the size by simply clicking on use remaining space   button (this will just use up the partition you added to group) or you  can make it smaller if you want to (just remember those warnings about  making it smaller than the amount space currently in use)


I wrote this very late - and I'm sorry if my clarity is lacking right now. Hope this helps.

---

### Post by Elfy on 2012-11-25
Nothing to do with you being a new user, but to do with the Tutes forums being closed to new threads.

Tutorials should be on the community wiki.

Thread Closed

---

