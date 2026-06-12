---
title: "Disks being kicked out of RAID1"
date: 2006-10-31
forum: Server Platforms
---

### Post by paaleivind on 2006-10-31
For some time now, we have been troubled by disks getting kicked out of the RAID array on our servers for no good apparent reason. At first we thought it might just be a few bad disks, and replaced them while we did several integrity checks on the failed disks. However, the same thing happened over and over, even with the new disks. And the disks we ran integrity checks on came out as clean 9 out of 10 times. This, combined with the frequency of the disks getting kicked out, has made us suspicious that there's something else that's the cause of our woes.

We use software RAID1 with SiL 3114 controllers, running on Ubuntu (AMD64) releases ranging from 5.10 to 6.06. The problem occurs with hard disks by various manufacturers, including Maxtor, WD and Samsung. This has also happened on servers that are not in production (i.e totally idle).

Some extracts from our logs when this has happened:
```
Oct 12 16:42:06 nu kernel: [ 3311.158089] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Oct 12 16:42:06 nu kernel: [ 3311.158098] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=47180134, high=2, low=13625702, sector=47179532
Oct 12 16:42:06 nu kernel: [ 3311.158113] ide: failed opcode was: unknown
Oct 12 16:42:06 nu kernel: [ 3311.158120] end_request: I/O error, dev hdb, sector 47179532
Oct 12 16:42:08 nu kernel: [ 3313.202410] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Oct 12 16:47:47 nu kernel: [ 3313.202419] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=47180134, high=2, low=13625702, sector=47179540 

Oct 29 08:35:31 midas kernel: [667744.573278] ata1: command 0x35 timeout, stat 0xd0 host_stat 0x61
Oct 29 08:35:31 midas kernel: [667744.603245] ata1: translated ATA stat/err 0xd0/00 to SCSI SK/ASC/ASCQ 0xb/47/00
Oct 29 08:35:31 midas kernel: [667744.664307] ata1: status=0xd0 { Busy }
Oct 29 08:35:31 midas kernel: [667744.664319] sd 0:0:0:0: SCSI error: return code = 0x8000002
Oct 29 08:35:31 midas kernel: [667744.664323] sda: Current: sense key: Aborted Command
Oct 29 08:35:31 midas kernel: [667744.664329]     Additional sense: Scsi parity error
Oct 29 08:35:31 midas kernel: [667744.664338] end_request: I/O error, dev sda, sector 490223244
Oct 29 08:35:31 midas kernel: [667744.664344] raid1: Disk failure on sda2, disabling device.
```
The funny thing is we're able to hotadd the disk that's been kicked out if we turn the power off and on, whereas this is not possible if we softboot it.

I'd appreciate any kind of advice or ideas as to what could be causing this.

---

### Post by ktulu1115 on 2007-05-10
Did you ever figure out the source of the problem?  I'm having the same identical issue with my RAID5 software array.  One drive in particular keeps failing out, swap in new ones, rebuild the array and same problem happens.  The RAID5 array is all Seagate 320gb SATA drives.  The RAID1 array in the same machine does not have any of the same issues - they are regular IDE drives.

Running AMD64 Feisty Server (originally Edgy but dist-upgraded).  Memtest reports no errors, going to run Seagate tools from latest UBCD to test out the first drive.

It ran fine for almost 5 months now without any problems and I'm starting to get stumped.

---

### Post by irvin on 2007-05-15
Hallo

I've a problem like this, after updating ubuntu 6.10 i have no more raid1, i have 2 disks.
here's the whole story:

My Problem is the VIA 8237 RAID Driver and Raid Tool

I'm also looking for Via Raid Drivers and the V-Raid Utility for Ubuntu 704. I want to use it as RAID 1. I use tthe VT8237A Chipset on a Asus M2V Mainboard.

After trying a lot of days to bring some kind of RAID working on 704 i found the RAID possibility in the alternative install of 704.
But that's only Softraid and the main problem is, that if one HD breaks, you can't boot the other alone. Or it is very comlicated.
But that's what I need, if one breaks, i can run the other.

So I decided to test the drivers for 6.10. It was hard, but after a lot of tries i finally installed the drivers for a RAID 1 on ubuntu 6.10 !
The I wanted to install the V-RAID Utility. After in installed, i wanted to run it but it didn't work. My PC begans to beeb like hell and ubuntu freezed completely !

I made a new boot and tried it again, same, endlees beeps from the Mainboard and complete freeze of ubuntu.
OK, i said, i got the raid, that's good for now.

Then I made the updates for Ubuntu. there are 181 updates, and i took them all. After the updates were installed, i made a boot and
the RAID Drivers were lost ! Now I had 2 drives. I tried to install the RAID drivers again but it doesn't worked for me. I took the alternative CD and made everything with the manual but the end didn't work for me.

So i made a complete new install and took NO updates ! I tried to install the V-RAID Utility again, but the same problem happened, beeps and freeze !

Did anybody made experiences like me, is there a possibilty to get the Utility to work or does anybody knows which updates I should not do if I want to keep my RAID drivers on the system ? It's impossible to get this from the 181 !?!

But the best thing would be a great RAID Driver and Utility for the Ubuntu 704 which I like very much !

update:

Any ideas or infos to this ? I'd like to setup a few machines on ubuntu with RAID1 but I'm not really satisfied with this update problem under 6.10. I did it now again and again and made updates but did not use the updates for the kernel going to 2.6.17-11 but it was always the same, RAID1 was deleted oder the driver. And it's very hard to setup the machine again and again only because there a a few updates which i really need (because of bugs).

Will there be a raid driver for the 7.04 ? Any chance ? Does anyone know which updates are "forbidden" if i want to use the raid1 on 6.10 ?
Bye
Irvin

---

### Post by ktulu1115 on 2007-05-15
@irvin:

It sounds like to me you are using a hardware RAID solution - is this correct?  If so, it would explain all your difficulties getting Linux to recognize the array.  In your situation I would recommend a software RAID array, the kernel has all the built-in drivers you'll ever need for it and won't have to face issues like you are having.  It's still possible to boot up from a RAID1 array even with a failed drive, it takes a little customization and tweaking form what I hear but certainly possible.  Best of luck.

---

### Post by irvin on 2007-05-15
Hi

Yes it's a "hardware" raid chip which is in the VIA VT8237A Southbridge 2x SATA (but everybody calls it software raid too - because it has now own cpu).

I tried the built in ubuntu Software raid, but that didn't really worked for me. Because the thing is, if one drive fails (i tested this a lot of times) I couldn't boot from the other only disk. I tried both ways hd1 and hd2. also i tried several rebuilt the one disk or to make a new bootloader but everything failed.

When I use the drivers from VIA i could install the RAID1. The I tried to boot from only one disk and it goes.
And normally, with the VIA Raid Tool you can take a new drive and mirror this to have again a working RAID1.

And that's what I need. Without any real hard work rebuilt a raid1 or even can boot the working hd if one fails.
Thanx for the help
Bye
Irvin

---

### Post by ktulu1115 on 2007-05-15
> **irvin said:**
> Hi

Yes it's a "hardware" raid chip which is in the VIA VT8237A Southbridge 2x SATA (but everybody calls it software raid too - because it has now own cpu).

I tried the built in ubuntu Software raid, but that didn't really worked for me. Because the thing is, if one drive fails (i tested this a lot of times) I couldn't boot from the other only disk. I tried both ways hd1 and hd2. also i tried several rebuilt the one disk or to make a new bootloader but everything failed.

When I use the drivers from VIA i could install the RAID1. The I tried to boot from only one disk and it goes.
And normally, with the VIA Raid Tool you can take a new drive and mirror this to have again a working RAID1.

And that's what I need. Without any real hard work rebuilt a raid1 or even can boot the working hd if one fails.
Thanx for the help
Bye
Irvin

With your experience with software RAID - did you try booting off of the /dev/md device instead of the drive itself?  I would highly recommend sticking with the software solution and trying to get it working, as it is far more powerful and flexible then a hardware solution - not to mention you don't have to worry about dealing with incompatible drivers or any kernel issues for the most part.  Asides from that, I don't have too much more advice for your situation.  Best of luck!

---

### Post by irvin on 2007-05-15
Hi

No, i don't think i tried booting from this /dev/md. After days of installing and testing etc. i gave up and used the Drivers cause i know them from windows and theyt worked great for me.
But I see the kernel problems coming every time i make an upgrade.
I think i'll try it again when I'm going to have enough power and time.
And as I just think about it, I didn't know how to install the boot loader to both disks.
I'll see what to do next, cause it would be better to use ubuntu 7.04 for me instead of 6.10.
Thanx
Irvin

---

### Post by ktulu1115 on 2007-05-15
> **irvin said:**
> Hi

No, i don't think i tried booting from this /dev/md. After days of installing and testing etc. i gave up and used the Drivers cause i know them from windows and theyt worked great for me.
But I see the kernel problems coming every time i make an upgrade.
I think i'll try it again when I'm going to have enough power and time.
And as I just think about it, I didn't know how to install the boot loader to both disks.
I'll see what to do next, cause it would be better to use ubuntu 7.04 for me instead of 6.10.
Thanx
Irvin

I'd suggest giving it a shot whenever you can - yes 'kernel' problems can appear using the "hardware" raid - just as an FYI, with software RAID, when one is assembled and brought online, the kernel itself creates a new block device just for the RAID itself, they start as /dev/md0 and increase numerically with each array you use.  From this point forth, when working with things like boot loaders and such, you must use the RAID block device instead of the drives themselves - pretend like /dev/hda1 and so on do not even exist anymore and were replaced by /dev/md0.  The kernel handles all the correct translation and maps the writes to both drives automatically through the software RAID module.  Hope this helps.

---

### Post by irvin on 2007-05-15
Hi

Thanx for the help, I just made a backup and I'm onto building an new raid1 withe the software raid.
I just found one mistake (or I think so) on my last few installations, may that was the point. I'll see what will happen.
Bye
Irvin

---

### Post by ktulu1115 on 2007-05-15
No problem - good luck!

---

### Post by irvin on 2007-05-15
Hi

I just made a new 7.04 RAID1 System and now have a grub bootload on each disk as i can see.
But if i disconnect one disc, I can't boot from the other alone. i tried normal and recovery but they hang after a few seconds. when i reconncect it boots normal. As I could see when i did the recovery mode, the system
has a problem to find der md1 oder evenb the fstab directory, something like that.

I thought I could select the md devices in the bootloader, but there's only the generic (recovery) and the memtest). How can i get there, boot from an md device, anybody knows that ?
Thanx
Irvin

Edit2: this is the complete list:

This is the last on the screen in recovery modus (in normal modus there's just a freeze:

mount: Cannot read /etc/fstab: No such file or directory
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/local-bottom ...
mount: Mounting /root/dev on dev/.static/dev failed: No such file or directory
Done.
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have sbin/init

BusyBox v.1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter "help"...

/bin/sh: can't access tty; job control turned off

(initramfs)

............ and then waiting for a command ?

---

### Post by irvin on 2007-05-15
Hi again

I found hundreds of problems with this error, but a lot come while installing 7.04 from Live CD.
There where many tipps which didn't help me. here are my menu.lst and fstab, they seem to be good, or ?

++++++++++++++++
menu.lst

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/md0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/md0 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
++++++++++++++++
fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=f6e99594-0e76-452a-a347-64ba511ce112 /               ext3    defaults,errors=remount-ro 0       1
# /dev/md1
UUID=7568e6b4-6c89-4e88-a375-5f3b78b10ab4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

++++++++++++++++
Bye
Irvin

---

### Post by irvin on 2007-05-16
Hi

I Think i finallyfound a solution (nearly no sleep). As I tried a lot more things, there was one magic word:

mdrun

I took one HD away and made the recovery boot. the i waited until the initramfs came and i had the command line

then: wrote mdrun and enter

the md0 stopped and started again. I don't know exactly was mdrun does but i think it checked if the two drieves ara available. it says something like running 1 from 2.

then i made a reboot (normal graphics) and the system started - perfect !

The I put the second hd2 on and started made the mdadm --add stuff and the hd's synced.

the I tried the same if the first hd fails, the grub bootloader was isntalled so also, mdrun... worked.

the i deleted the aother hd, started made exactly same partitions and the --add stuff.
they resynced, everything works now, hopefully there's no problem again if the really fail sometime and the kernel is changed again and again... we will see.
Many thanx for the support and the "good words" to try it with the software raid.

I was so in the windows thing where everything went great in the last years with the VIA Raid drivers and software, but I really was not in the probs with the kernel changes.
So you can never be sure if your system will boot again in raid after updates.
Bye
Irvin

---

