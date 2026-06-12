---
title: "Ubuntu Server 12.04 LTS RAID 5 issue"
date: 2012-10-13
forum: Server Platforms
---

### Post by Blade Runner on 2012-10-13
Hi

First I'd like to apologise if my question has already been answered elsewhere - I've searched and not been able to find a solution as yet.

Here's my setup:

Gigabyte GA-Z77X-UD5H Wif Mobo
Intel Core i7 3770K 3.5GHz
3 x Seagate 3TB Barracuda Hard Drive - 3.5" SATA-III - 7200RPM 64MB Cache

I've enabled RAID in the BIOS on the Mobo and installed Ubuntu Server 12.04 LTS. During install the Fake RAID was recognised and Ubuntu 12.04 LTS was installed to the array, however, it only recognised 1.6TB whereas it should have recognised around 5.7TB.

On further Googling and trawling through forums I read that MBR partitions only recognise upto 2TB and I need to use GPT partitions and would be better served by using Software RAID as opposed to the Fake RAID on the Mobo BIOS.

I've spent a good few hours trying to find relevant and correct information as to the best way to install Ubuntu Server 12.04 LTS with RAID 5 on GPT partitions. Some forums suggest using a live CD to boot into Gparted to configure the GPT partitions, but don't elaborate on how to do it :P

What I need is the following:
Howto setup the hard drives using GPT partitions
What sizes and partitions need to be created, bearing in mind they're 3TB hard drives
The correct steps needed to enable Software RAID 5

Many thanks in advance

BR ):P

---

### Post by darkod on 2012-10-13
First, now you have to get rid of the fakeraid meta data that's on the disks right now. Enter the bios and change the sata mode from raid to ahci.
Then boot with ubuntu desktop live cd into live mode, open terminal and for every disk run:
sudo dmraid -Er /dev/sdX

replacing X with a,b,c for all three disks. That will clear the meta data.

You can write a gpt table using the server installer, but since you are already in live mode it's easier to do it right away. You can use parted, again for all three disk do:
```
sudo parted /dev/sda
mklabel gpt
unit MiB
mkpart GRUB 1 2
set 1 bios_grub on
quit
```

That will write new blank gpt table and create the small bios_grub partition of 1MiB that you need for grub2 to install on gpt disks. Do that for all three disks.

After that you can boot the server cd and start the installer. Choose manual partitioning and create the partition sizes you want for the raid devices. In the Use As field for the partition select Physical device for RAID.

After you have all of them created as partitions for raid, go in the option above the partitions list into Configure software raid.

There you can create the devices, choose the raid level (type) and the partitions that it would include.

And that's it more or less.

For the partitions sizes I can't help much since it depends on your usage. But with disks of 3TB it's often better to have a smaller raid device for / or /boot so that the boot files are not thrown around the big disks.

---

### Post by Blade Runner on 2012-10-15
Hi darkod

Many thanks for the reply.

I still have a few issues though and wonder if you could steer me in the right direction.

To recap, I have three 3TB hard drives that I wish to set up with software RAID5.

I've followed your instructions and created a new blank gpt table and created the small bios_grub partition of 1MiB on each of the 3 disks. I then created a primary partition and a swap partition on each of the three disks.

I tried setting each of the partitions to Physical Device for RAID, however, this changed the partition flag so it was no longer root or swap. When I selected to configure Software RAID it then asked me to select just three partitions and this is where I got stuck. Which three should I select? I've tried selecting each of the three primary partitions but I get an error message that there is 'No root file system defined.'

I'm almost there I'm sure, but not quite! I've attached screenshots which I hope will help.

Once again, many thanks for your help.

BR

---

### Post by darkod on 2012-10-15
No, you made a mistake with root and swap.

Make new gpt tables again and create the bios_grub (because on two of the disks they got messed up according to one of the images).

After that, start the server OS installation and create the equal partitions that you are planning for root and swap, BUT when you are creating the partition in the Use As select device for RAID (not ext4 or swap area).

So, after that the existing partitions on all three disks should look like:
#1 -> 1MB bios_grub
#2 -> 3TB raid
#3 -> 34GB raid

After that, go into Configure Software RAID, select for the md0 device raid5, when asked which devices select sda2, sdb2 and sdc2. That will create one raid device.

Then select to create another, md1, and use sda3, sdb3 and sdc3. Note that when selecting items in text menus you do it with Space bar and you will see the * mark when selected. If you hit Enter thinking it will select it, it will actually be understood as the OK button and the menu might closed with nothing selected.

After you create md0 and md1 and you go back to the partitioning menu, you will see those two new devices. Now select the md0 (bigger one), and in Use As select ext4 and mount point /. Then select the smaller one and select Use As swap area.

You're good to go. :)

---

### Post by Blade Runner on 2012-10-15
Hi darkod

That got it, thank you so much!

Finally, I can start to install and build my server :p

BR

---

### Post by talung on 2012-10-18
I was having issues with partitioning and followed your advice for a new Raid 5 setup using 4x 2TB drives.

Everything is setup as stated in above posts, and the install went through fine.

The issue I am currently facing is that the system will not boot.  It says there is no boot device.  I know that grub installed.  My bios is set to AHCI. (not IDE or RAID).  All structures look correct.

Any idea why it will not boot? is there something else I am missing?  Installing Grub from live CD for example.. just a bit lost at the moment.

Thanks

---

### Post by darkod on 2012-10-18
> **talung said:**
> I was having issues with partitioning and followed your advice for a new Raid 5 setup using 4x 2TB drives.

Everything is setup as stated in above posts, and the install went through fine.

The issue I am currently facing is that the system will not boot.  It says there is no boot device.  I know that grub installed.  My bios is set to AHCI. (not IDE or RAID).  All structures look correct.

Any idea why it will not boot? is there something else I am missing?  Installing Grub from live CD for example.. just a bit lost at the moment.

Thanks

Some boards don't boot if they can't see a boot flag on at least one primary partition. Linux doesn't use the boot flag like windows, and by default I am not sure it puts one anywhere.

Also, if you use gpt tables too, I'm not sure if this boot flag would interfere with the bios_grub flag so it might be best to try it on another partition.

If you are willing to do a new install, when you configure the mdX device to be used as root, there is also option to select to make it bootable (boot flag). Use that. And see if it helps.

If you don't want to reinstall, you can also use the ubuntu desktop live cd, boot the machine in live mode, open Gparted and set the boot flag on any of the primary raid partitions, just so that the motherboard can see a boot flag existing. In Gparted you manage the flags by right-clicking a partition and selecting the Manage Flags option.

---

### Post by talung on 2012-10-18
[QUOTE=darkod;12301868
Also, if you use gpt tables too, I'm not sure if this boot flag would interfere with the bios_grub flag so it might be best to try it on another partition.

If you are willing to do a new install, when you configure the mdX device to be used as root, there is also option to select to make it bootable (boot flag). Use that. And see if it helps.

If you don't want to reinstall, you can also use the ubuntu desktop live cd, boot the machine in live mode, open Gparted and set the boot flag on any of the primary raid partitions, just so that the motherboard can see a boot flag existing. In Gparted you manage the flags by right-clicking a partition and selecting the Manage Flags option.[/QUOTE]

Hi Darkod,

Thanks for the reply.  This is a new install, so its no issue to reinstall it again.  I have been unable to set the boot flag in the raid partition at all.  Thats what led me to your post.  I have also been unable to partition it.. Its just one big volume. (2 raid sets as the above described)

I am using GPT, and followed the above instructions exactly.  Would using gparted create issues as it does not recognise gpt partitions.  I will try that anyway.

At the moment, I am leaning towards having 1 drive out of the raid for OS and rest in the raid.. will waste a lot of space, so hesitant to do this.

BTW, on a very new ASUS mobo with usb 3 etc.. so maybe thats an issue with the software raid.

---

### Post by darkod on 2012-10-18
Try putting it on the small bios_grub partition, one of them. For example on the first /dev/sda disk.

If you used live mode and parted first to prepare the disks, when setting the bios_grub flag add one more command to that list:
```
set 1 boot on
```

See if that helps.

The no boot device message is usually bios message, not OS so it looks like your board is doing it. And make sure uefi is not enabled on the board.

---

### Post by talung on 2012-10-18
The bios did indeed have UEFI & Legacy turned on.  I have turned that off so that it is only legacy. I am also going to start from the beginning with clean disks and see if that works.

Complete recreation of drives as per these forum posts.

I hope this works now.

Thanks

---

### Post by talung on 2012-10-18
> **talung said:**
> 
I hope this works now.



It Does!  it works.  I think the root of the problem was the UEFI turned on in the BIOS.  Thanks a ton Darkod... been at this for many many hours trying to figure it out.

Here is a virtual beer.
:guitar::P

---

### Post by potmos79 on 2013-01-26
Thank you so much, i have been searching and trying for two days to get my computer to boot.
After updating the bios, so that i could disable uefi, which wasnt an option for me. Repartitioning like you said it worked like a charm.

---

