---
title: "HowTO: Btrfs Root Installation"
date: 2010-01-24
forum: Tutorials
---

### Post by ibuclaw on 2010-01-24
_**[CENTER][COLOR="Sienna"][SIZE="6"]HowTO: Btrfs Root Installation[/SIZE][/COLOR][/CENTER]**_

[COLOR="Sienna"][SIZE="5"]Foreword[/SIZE][/COLOR]
Btrfs is a new copy on write file system for Linux aimed at implementing advanced features while focusing on fault tolerance, repair and easy administration. Initially developed by Oracle, Btrfs is licensed under the GPL and open for contribution from anyone.

Linux has a wealth of file systems to choose from, but we are facing a number of challenges with scaling to the large storage subsystems that are becoming common in today's data centers. File systems need to scale in their ability to address and manage large storage, and also in their ability to detect, repair and tolerate errors in the data stored on disk. 

*Source: [http://btrfs.wiki.kernel.org](http://btrfs.wiki.kernel.org)*

[COLOR="Red"][B]The steps and procedures in this guide have been tested on and work with Ubuntu 9.10 - Karmic Koala, and Ubuntu 10.04 - Lucid Lynx. Any other release is not guaranteed to work at all.


Please bear in mind that Btrfs is a development file system, as such, you will experience crashes, glitches, and possible loss of data. Do not use it for production use[/B][/COLOR]

OK, I think that has scared away most users. Now for those crazy people who remain. (You Lucid users know who you are). :)


**Updates for Maverick users:**
[LIST]
[*]Booting into a Btrfs system no longer requires patching of GRUB. So long as you have a separate partition to boot (recommended format ext2), things are said to go smoothly.
[*]As of 2.6.34, Btrfs has a new and enhanced utility tool to control and show statistics of the Btrfs partition. It's usage is not covered in this guide.
[/LIST]

**Updates for Natty users:**
[LIST]
[*]The Ubuntu installer seamlessly allows you to use Btrfs now, and GRUB has full support, meaning it is no longer necessary to have a separate /boot anymore.
[/LIST]

[COLOR="Sienna"][SIZE="5"]Part 1: Installation[/SIZE][/COLOR]
By and far, the most simplest method is to convert an already existing installation from Ext3/Ext4 to Btrfs. Although an installation from scratch probably produces better behaviour and will give you the option for choosing between how the file system is setup - options you cannot change after creation - ie: raid level.


[COLOR="Sienna"][SIZE="4"]Setting up the Base Install[/SIZE][/COLOR]
So, what we do is go through the installation process as normal, and when we reach the Partition stage, select the "Advanced" option to specify manually.

[COLOR="Sienna"][SIZE="3"]Separate /boot[/SIZE][/COLOR]
First, we create a /boot partition formatted as an ext2 - this is important if we want to boot the OS!
500MB in size should be sufficient enough.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144838&stc=1&d=1264365324[/IMG]


How you go about your business after that doesn't really matter, but you may end up with something like this afterwards.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144839&stc=1&d=1264365324[/IMG]


Ensure that you **make a note** of which file system will be mounted as /, as you will need that info when you convert it.

[COLOR="Sienna"][SIZE="3"]Post Installation[/SIZE][/COLOR]
The rest is everything as usual, and once the installation is complete, congratulations, the easy bit is done! Select "**Continue Testing**" so we can now traverse onto the hard bit.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144840&stc=1&d=1264365324[/IMG]


Firstly, edit the sources so that the universe is included in them. This can be done via "**System -> Administration -> Software Sources**"

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144841&stc=1&d=1264365324[/IMG]


Reload the sources after closing, and next, open a terminal. Now we can begin on the dirty work. :D


[COLOR="Sienna"][SIZE="4"]Converting Ext4 to Btrfs[/SIZE][/COLOR]

[COLOR="Sienna"][SIZE="3"]The Physical Conversion[/SIZE][/COLOR]
As my system was installed on /dev/sda5, that is the one I'll be specifying in this guide. If yours is different, change the path as needed.

In order to convert the file system, we require btrfs-tools to be installed.
```
sudo apt-get install btrfs-tools
```
The conversion, thankfully, is elementary. 
```
sudo btrfs-convert /dev/sda5
```
The not so elementary bit is reconfiguring the boot process to play nice with the file system.

First though, we re-mount all file systems as you would expect them to be as if you were booted into it.
```

sudo mount /dev/sda5 /mnt
sudo mount /dev/sda1 /mnt/boot
for fs in proc sys dev dev/pts; do sudo mount --bind /$fs /mnt/$fs; done

```
Now we chroot into the file system.
```
sudo chroot /mnt
```
From here on - until we reboot - we will run all commands inside the chroot.

[COLOR="Sienna"][SIZE="3"]Update Fstab[/SIZE][/COLOR]
The conversion process creates a new UUID for the partition, as such this requires updating.

To obtain the new UUID, run:
```
blkid /dev/sda5
```
Make a note, then edit /etc/fstab
```
nano /etc/fstab
```
I've highlighted the areas of interest that require changing - don't forget to update the file system type too.
**Before**:
```

# / was on /dev/sda5 during installation
UUID=e03cb3cc-8470-4ee6-a18a-b49da45c6f21 /             ext4    error=remount-ro 0      1

```
**After**:
```

# / was on /dev/sda5 during installation
UUID=[COLOR="Red"]4be84d08-94cb-4013-ae0b-ce1d72d96db1[/COLOR] /             [COLOR="Red"]btrfs   defaults        [/COLOR] 0      1

```

[COLOR="Sienna"][SIZE="3"]Hack GRUB2[/SIZE][/COLOR]
At this current time of writing, Grub2's detection method of using stat() cannot detect a Btrfs file system - [see here why]("http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg02875.html") - so we need to make it so Grub2 detects the it every time you run **update-grub**.

As it turns out Grub0.97 can detect it just fine, but if downgrading is out of the question, I've written a nice little patch that backports the old grub detection method.
All you need to do is install patch, download and setup the correct diversions - so they don't get overwritten if an upgrade were to occur.
```

apt-get install patch
wget http://launchpadlibrarian.net/36483885/legacy_detection.patch
dpkg-divert --local --add /usr/sbin/grub-mkconfig
dpkg-divert --local --add /usr/lib/grub/grub-mkconfig_lib

```
Then open the patch for editing
```
nano legacy_detection.patch
```
and search and replace the two lines specified below in the file as seen highlighted in red, ignoring the rest of the file.
**Before**:
```

+++ grub2-1.97~beta4/util/grub-mkconfig.in	2009-12-05 21:42:51.908543561 +0000
...
+++ grub2-1.97~beta4/util/grub-mkconfig_lib.in	2009-12-05 21:42:18.876544591 +0000

```
**After**:
```

+++ [COLOR="Red"]/usr/sbin/grub-mkconfig[/COLOR]	2009-12-05 21:42:51.908543561 +0000
...
+++ [COLOR="Red"]/usr/lib/grub/grub-mkconfig_lib[/COLOR]	2009-12-05 21:42:18.876544591 +0000

```
Once saved, you can apply the patch.
```
patch -p0 < legacy_detection.patch
```
It may give some feedback to you on "Hunk Succeeded", that is all OK. If it were to say "Hunk Failed", then you'd know that the patch didn't apply as expected.

[COLOR="Sienna"][SIZE="3"]Update Initramfs[/SIZE][/COLOR]
Next, we hook btrfs into the boot process. It helps if btrfs-tools is installed first.
```
apt-get install btrfs-tools
```

Now we start creating our files.

First, is the hook
```
nano /usr/share/initramfs-tools/hooks/btrfs
```
Paste in the following contents and save.
```

#!/bin/sh -e
# initramfs hook for btrfs

if [ "$1" = "prereqs" ]; then
    exit 0
fi

. /usr/share/initramfs-tools/hook-functions

if [ -x "`which btrfsctl`" ]; then
    copy_exec "`which btrfsctl`" /sbin
fi

```
Second are the modules
```
nano /usr/share/initramfs-tools/modules.d/btrfs
```
Paste in the following contents and save.
```

# initramfs modules for btrfs
libcrc32c
crc32c
zlib_deflate
btrfs

```
Last is the Premount script.
```
nano /usr/share/initramfs-tools/scripts/local-premount/btrfs
```
Paste in the following contents and save.
```

#!/bin/sh -e
# initramfs script for btrfs

if [ "$1" = "prereqs" ]; then
    exit 0
fi

modprobe btrfs

if [ -x /sbin/btrfsctl ]; then
    /sbin/btrfsctl -a 2>/dev/null
fi

```

Then make the following files executable.
```

chmod +x /usr/share/initramfs-tools/scripts/local-premount/btrfs
chmod +x /usr/share/initramfs-tools/hooks/btrfs

```
And to round up the entire process, rebuild the ramdisk and update grub.
```

update-initramfs -u -k all
update-grub

```
Et Voila! We can now reboot our system.

When you boot up, you can see proof of your new btrfs system as per below!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144842&stc=1&d=1264365324[/IMG]



[COLOR="Sienna"][SIZE="5"]Part 2: Usage[/SIZE][/COLOR]
[COLOR="Red"]**NOTE: If you are running on Karmic**[/COLOR]
To use some of the commands in this section, it's recommend that you acquire the latest release.
And if that isn't enough of an excuse, it's recommended because of the bug fixes too - [see here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/481404").

I already have a repository setup for **Karmic** with the correct packages inside, feel free to add and install via the following method.
```

sudo add-apt-repository ppa:ibuclaw/ppa 
sudo apt-get update
sudo apt-get install btrfs-tools btrfs-kernel-source
sudo update-initramfs -u -k all
sudo reboot

```
Once rebooted, I recommend running:
```
sudo btrfs-vol -b /
```
Before doing anything else. What this does, is a balance operation that reads in all of the FS data and metadata and rewrites it across the file system. As such, it may take some time.

OK, with that done, time to try out some of the cool things you can do.


[COLOR="Sienna"][SIZE="4"]Features List[/SIZE][/COLOR]

[COLOR="Sienna"][SIZE="3"]Incremental backup and Writable snapshots[/SIZE][/COLOR]
Snapshots are integrated into the file system with no extra work done. This means that you don't need to wait around for hours just for an image to be created, the snapshot acts more like a baseline, and changes to the Live System get written elsewhere on the disk whilst the Snapshot stays static.

To create a snapshot of the root subvolume.
```

cd /
sudo btrfsctl -s snapshot.root /
ls /snapshot.root

```
The first argument is the snapshot name, the second is the subvolume you wish to snapshot. The snapshot is created in the directory you are currently residing in.

And as an exercise you can try deleting and recovering files on your Desktop.
To recover, a simple 'cp -a' should do the trick, but rsync would be the better option.
```
sudo cp -a /snapshot.root/home/iain/Desktop ~/
```

Snapshots are writeable, meaning that you can instead change data in the snapshot without affecting the Live System also.

This can be useful for example, when you want to have a chroot for compiling, or running certain applications in their own environment.
```
sudo chroot /snapshot.root
```
If this is not the behaviour you wish to have, then you can chmod the directory to prevent normal users from tampering it.
```
sudo chmod 700 /snapshot.root
```

Lastly, to delete snapshots:
```
sudo btrfsctl -D snapshot.root /
```
The first argument is the snapshot name, the second is the path of the directory the snapshot resides in.

[COLOR="Sienna"][SIZE="3"]Subvolumes (separate internal file system roots)[/SIZE][/COLOR]
 Unlike snapshots, subvolumes are **immutable**, meaning that once you create one, it can't be removed unless you reformat the volume.
The best use I've found for subvolumes is to apply finer grain snapshots throughout the file system, rather than one great one for /.

One example can be the /home directory.
In recovery mode, this can be implemented with the following:
```

cd /
mv /home /home.old
btrfsctl -S home /

```
Then we set the correct permission for the subvolume (default is 700), and move our data in.
```

chmod 755 /home
mv /home.old/* /home
rmdir /home.old

```

Then to create a snapshot:
```

btrfsctl -s snapshot.home /home
ls /snapshot.home

```

[COLOR="Sienna"][SIZE="3"]Compression and other Mount options[/SIZE][/COLOR]
Wouldn't recommend trying it yet (although I'm pretty certain I saw a speed increase after enabling it), but feel free to add compress to the fstab file.
```
UUID=4be84d08-94cb-4013-ae0b-ce1d72d96db1 /             btrfs   defaults[COLOR="Red"],compress[/COLOR] 0      1
```
And remount using:
```
sudo mount -o remount /
```

**NOTE**: The compress option is a type of smart compression, as in it was compress highly compressible files, but back off and blacklist incompressible content.
Also, please bare in mind the following caveats:
[LIST]
[*]If compression for a given set of pages fails to make them smaller, the file is flagged to avoid future compression attempts later. To get around this, there is 'compress_force' - which will force compression, even at horrendous cost to performance (thank-you jdong).
[*]The looking up of the actual size of the compressed file is currently unimplemented.
[*]With compression enabled, your system may deadlock all IO operations if under heavy read/write duty.
[/LIST]


See here for more supported options: [http://btrfs.wiki.kernel.org/index.php/Getting_started#Mount_Options](http://btrfs.wiki.kernel.org/index.php/Getting_started#Mount_Options)

[COLOR="Sienna"][SIZE="3"]Integrated multiple device support[/SIZE][/COLOR]
Another cool feature is the ability to have a file system that spans two, or more partitions or devices.

If possible, try this nice exercise to see the before and after of the size of /
```

df -h /
sudo mkfs.btrfs /dev/sdb
sudo btrfs-vol -a /dev/sdb /
df -h /

```
And it should have increased!

To balance the load between the devices:
```
sudo btrfs-vol -b /
```
By default, meta data will be mirrored across two devices and file system data will be striped across all of the devices present.

Removing devices uses the same logic.
```

sudo btrfs-vol -r /dev/sdb /
df -h /

```
And notice that the size of / has now shrunk again.
For a more detailed look into it, [see here]("http://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices").

[COLOR="Sienna"][SIZE="3"]Offline file system check[/SIZE][/COLOR]
Self explanitory, really.
```
sudo btrfsck /dev/sda5
```
**NOTE**: btrfsck is **NOT** an online checker. **IT IS OFFLINE ONLY**, contrary to what the documentation said at one point. Running btrfsck online can lead to filesystem corruption! (thank-you for pointing this out jdong).

[COLOR="Sienna"][SIZE="3"]Online file system defragmentation[/SIZE][/COLOR]
Lastly, the feature everyone has been waiting for...
```
sudo btrfsctl -d /
```
The argument being the location of the subvolume you wish to defragment.
Quite boring, really. There is not even a progress bar. ;)


For more small hints that I have not included, see the Btrfs wiki at [http://btrfs.wiki.kernel.org/](http://btrfs.wiki.kernel.org/)



[SIZE="5"][COLOR="Sienna"]Part 3: Common Errors and HowTOs[/COLOR][/SIZE]
Most pitfalls can be avoided if you treat your system as a stable one.
ie: Set it so your system only scans for **Security Updates**, and checks **once every fortnight**.


[COLOR="Sienna"][SIZE="4"]udev failing to configure[/SIZE][/COLOR]
If you were to upgrade udev, at all, you **will** run into this.
At this point in time, I have no explanation for why this happens, but you will know what it is when you see it:
> 
udevadm trigger is not permitted while udev is unconfigured.
udevadm settle is not permitted while udev is unconfigured.
Gave up waiting for root device.

If you get this then the only fix is to reinstall udev. Boot into LiveCD, open a terminal and mount all file systems:
```

sudo mount /dev/sda5 /mnt
sudo mount /dev/sda1 /mnt/boot
for fs in proc sys dev dev/pts; do sudo mount --bind /$fs /mnt/$fs; done

```
chroot into the file system
```
sudo chroot /mnt
```
and reinstall.
```

aptitude reinstall udev
update-initramfs -u -k all

```
Then reboot, and everything should be resolved again.


[COLOR="Sienna"][SIZE="4"]Symlinks missing in /dev[/SIZE][/COLOR]
Again, the cause of this is unknown, but it's effect does crop up from time to time with various applications complaining.

The workaround is to edit /etc/rc.local
```
sudo nano /etc/rc.local
```
And put in the following before **exit 0**
```
find /lib/udev/devices -type l -exec cp -a "{}" /dev/ \;
```


[COLOR="Sienna"][SIZE="4"]General Protection faults[/SIZE][/COLOR]
This most likely happens when libraries have mysteriously become corrupt/altered.
See the below output for when X refused to start at one point:
> 
[ 1 157.189485] Xorg[2309] general protection ip:4f6e1b sp:bfd1b32c error:0 in libc-2.10.1.so[413000+142000]

The workaround is just to reinstall the affected library, in my case, I ran:
```
sudo aptitude reinstall libc6 libc6-i686
```


[COLOR="Sienna"][SIZE="4"]GTK Themes Change After System Update[/SIZE][/COLOR]
Not sure why this happens, but the GConf database goes corrupt sometimes after a big system update.
This is always rectified by running:
```
sudo gconftool-schemas --register-all
```
And a logout / login.


[COLOR="Sienna"][SIZE="4"]Separate Btrfs /home Subvolume[/SIZE][/COLOR]
I covered the creation of subvolumes in this guide earlier. What I didn't cover was that you can use them similarly to actual partitions.

Going back on creating a subvolume for /home, You can also go on to create an entry in /etc/fstab for the new subvolume.
```

# / was on /dev/sda5 during installation
UUID=4be84d08-94cb-4013-ae0b-ce1d72d96db1 /             btrfs   defaults         0      1
[COLOR="Red"]# /home
UUID=4be84d08-94cb-4013-ae0b-ce1d72d96db1 /home         btrfs   defaults,subvol=home 0      1[/COLOR]

```
And it will be mounted as a separate partition every time on boot.

This is useful for when, say, you need to boot into a recovery snapshot that doesn't include /home or some other need partition directories.



[COLOR="Sienna"][SIZE="5"]Epilogue[/SIZE][/COLOR]
As I type this, I am sitting at a workstation with a Btrfs / installation of Ubuntu, compromised of two 250GB hard drives with the file system spanning across both in a RAID0 style format. As I never use this workstation often, I downloaded about 20GBs worth of native Linux games just for the odd occasions where I require some action to stimulate myself back into focus.

An interesting idea I conjured up whilst writing this (but haven't gotten round to testing yet), is that it may be possible to have separate installations of Linux inside their own snapshots/subvolumes.

Which is cool - not quite amazing yet, but cool. I have always find an enjoyment in using fringe and bleeding edge technology, it's like looking at a mirror which reflects back a vision of the world some time in the future. Using Btrfs over the past 3 months has convinced me enough to convert all my workstations to it - with the exception of my Netbook. I kind of see Ext4 as just another file system to get by on, whereas Btrfs is a tool to get work done on. And while the occasional fun hiccup occurs, I shall always regard this file system as a glimpse of what is to come...

Tips and Suggestions welcome.

---

### Post by iggykoopa on 2010-02-04
Thanks for the awesome writeup. I was using a similar setup, but had to downgrade to grub-legacy before, the patch fixed everything for me :D I'm mainly using it on my laptop with an ssd for the compress option, but on lucid it actually seems faster than ext4 now.

---

### Post by ViperScull on 2010-02-04
Just awesome mate.

iggykoopa, indeed, btrfs is faster than ext4 with kernel 2.6.33.

ext4 speed has been decreasing since 2.6.29 in exchange of reliability.

---

### Post by marksquare on 2010-02-05
Why do you have to patch grub?

If I'm correct you have a boot partition in ext2 and grub only sees that one (without any patch). 
On loading Grub will boot the the kernel and initrd from boot partion. After that the kernel will mount your btrfs partition.

Bye
Marco

---

### Post by marksquare on 2010-02-05
Sorry for the noise.

I found a good explanation here:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540786](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540786)

Good article.

Thanks
Marco

---

### Post by ibuclaw on 2010-02-05
> **marksquare said:**
> Why do you have to patch grub?

If I'm correct you have a boot partition in ext2 and grub only sees that one (without any patch). 
On loading Grub will boot the the kernel and initrd from boot partion. After that the kernel will mount your btrfs partition.

Bye
Marco

As I also explained in the OP, grub2 uses stat() to determine which /dev/* is the correct one for the path /.
Since btrfs is more like a block device, rather than an actual filesystem, grub2 fails to stat it correctly.

Another link to look at is this: [http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg02875.html](http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg02875.html)

Regards
Iain

---

### Post by jdong on 2010-02-06
Nicely written! I've been running btrfs as my root for a couple months now and this guide says everything I'd have to say about doing so.


Note one **very very important correction**: btrfsck is **NOT** an online checker. **IT IS OFFLINE ONLY**, contrary to what the documentation said at one point. Running btrfsck online can lead to filesystem corruption! (Later git releases of btrfs-tools does include a mounted filesystem check, but in Karmic it does not)

---

### Post by mahasamoot on 2010-02-09
Thanks for the howto!  I have a few of questions:

[LIST=1]
[*]I'm using Karmic, but I updated to the mainline kernel: [INDENT]thomas@Aristotle:~$ cat /proc/version Linux version 2.6.32-02063207-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #02063207 SMP Fri Jan 29 10:09:41 UTC 2010[/INDENT] Do I still need to do the karmic update step, and if so how would that change?

[*]I'm using luks underneath btrfs.  I've got more drives to add, but how will it know it needs to unlock the other drives to open the root partition?  It's only unlocking /dev/sda3 during boot, because /dev/sdb2 and /dev/sdc2 aren't being used.  From the fstab
[INDENT]/dev/mapper/sda3_crypt /        btrfs   error=remount-ro,compress 0     1[/INDENT] 
it looks like it just needs the one.  Also, they all have the same passphrase, so I'd like to unlock them all at once... which mandriva did, but kubuntu doesn't.  Ideas?

[*]I made a subvolume for /home, as per your instructions... I've seen elsewhere that subvolumes are put in the fstab.  Is that normally needed?
[/LIST]

---

### Post by antiram on 2010-02-11
the mount option "error=remount-ro" is useless and boot with 2.6.33 and btrfs fail with this option.

@ibuclaw
why do you not rebase your btrfs-tools ppa against version 0.19-8 from lucid? It corrects the path from bin to sbin.

here is a patch for fsck at boot time, because -a option is missing.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=567681](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=567681)

---

### Post by ibuclaw on 2010-02-12
> **antiram said:**
> the mount option "error=remount-ro" is useless and boot with 2.6.33 and btrfs fail with this option.

I've never had issue with Karmic, but I guess using "defaults" has no harm.


> **antiram said:**
> @ibuclaw
why do you not rebase your btrfs-tools ppa against version 0.19-8 from lucid? It corrects the path from bin to sbin.

here is a patch for fsck at boot time, because -a option is missing.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=567681](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=567681)
I actually did this 12 days ago (looking at the changelog). I guess I never got round to uploading it to the ppa - partly because I have been on holiday for the past fortnight.

Thanks for that patch too. I'll review it as soon as I get a chance. :)

Regards
Iain

---

### Post by ibuclaw on 2010-02-14
> **antiram said:**
> here is a patch for fsck at boot time, because -a option is missing.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=567681](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=567681)

OK, I've had a look, and the patch is absolutely horrible (in my option).
I've included it anyway, but I may change it to something proper if I get time.

Regards

---

### Post by degarb on 2010-02-22
I could not get compression to work.

anyone up to writing a real manual for newbies to get seamless compression.

Like what to add to fstab, how , and how to find out what.   

How to keep the os from mounting before you do a mount o compress.

I got mkfs to work and files to load. but not to compress.  I added a gig to two gig drive and was left with a gig free. I am assuming it didn't work.

---

### Post by ibuclaw on 2010-02-22
> **degarb said:**
> I could not get compression to work.

anyone up to writing a real manual for newbies to get seamless compression.

Like what to add to fstab, how , and how to find out what.   

How to keep the os from mounting before you do a mount o compress.

I got mkfs to work and files to load. but not to compress.  I added a gig to two gig drive and was left with a gig free. I am assuming it didn't work.

Put "compress" as an option in fstab.

There are some caveats with btrfs compression, now in the guide, that I have not mentioned prior, and if a file doesn't seem to compress, then the file system is only working to design.

Regards
Iain

---

### Post by degarb on 2010-02-22
> **ibuclaw said:**
> Put "compress" as an option in fstab.

There are some caveats with btrfs compression, now in the guide, that I have not mentioned prior, and if a file doesn't seem to compress, then the file system is only working to design.

Regards
Iain


I hit mount I can see my external usb drive  on sdb1

Thanks.  Unfortunately, when I do blkid -o value -s UUID /dev/sdb1

or even 

blkid -o value -s UUID /dev/sdb1


Nothing is printed out, nor is there any naturally occuring fstab reference to sdb anywhere. there is a natural reference to the internal drive sda1 and the swap sda5.

All i am interested in is seemlilessly (invisible to apps) compressing a drive or folder, like ntfs.  Little reference to it.  You refer to compress  0 in fstab,  but why not compress 9.   I also wonder about spacing in this.

---

### Post by degarb on 2010-02-22
maybe blkid doesn't work with usb devices so the compression wont work on external drives?


[FONT=monospace][/FONT]

---

### Post by ibuclaw on 2010-02-22
> **degarb said:**
> All i am interested in is seemlilessly (invisible to apps) compressing a drive or folder, like ntfs.  Little reference to it.  You refer to compress  0 in fstab,  but why not compress 9.   I also wonder about spacing in this.
There is no level of compression in btrfs, only compress, or no compress. You are confusing the 4th column with the 5th column of the fstab line.

> **degarb said:**
> maybe blkid doesn't work with usb devices so the compression wont work on external drives?

try:
```
sudo blkid /dev/sdb1
```
No fancy options. You should see 'UUID=1234-5678' outputted somewhere.

Regards
Iain

---

### Post by jdong on 2010-02-23
> **ibuclaw said:**
> There is no level of compression in btrfs, only compress, or no compress. You are confusing the 4th column with the 5th column of the fstab line.


try:
```
sudo blkid /dev/sdb1
```
No fancy options. You should see 'UUID=1234-5678' outputted somewhere.

Regards
Iain

To clarify, nowadays in btrfs there are two compress methods:

** -o compress**: Smart compression -- compress highly compressible files, but back off and blacklist incompressible content.

** -o compress_force**: Forced compression. Even at horrendous cost to performance, apply compression.


Both algorithms use zlib (gzip) compression at default level -- this is not tunable yet.

---

### Post by degarb on 2010-02-23
> **jdong said:**
> To clarify, nowadays in btrfs there are two compress methods:

** -o compress**: Smart compression -- compress highly compressible files, but back off and blacklist incompressible content.

** -o compress_force**: Forced compression. Even at horrendous cost to performance, apply compression.


Both algorithms use zlib (gzip) compression at default level -- this is not tunable yet.


These are for manually mounting.  what would the fstab equivalent be?

---

### Post by ibuclaw on 2010-02-24
> **degarb said:**
> These are for manually mounting.  what would the fstab equivalent be?

Just add "compress" or "compress_force" (thank-you again jdong for further enlightenment) in the 4th column of your fstab file.

This is outlined in the guide under "Compression and other Mount Options"

Regards
Iain

---

### Post by degarb on 2010-02-24
I am fuzzy on what happens to file sizes and readability when you mount/toggle compression. 

I seem to be thinking/assuming: if off, new files aren't compressed, when mounted on, then new files are written with compress but old files will be not be compressed.  Now if toggled off, are these compressed files readable and transparently working?  But what about files the a vdi that "grows"  if you create it in compressed drive, the turn off compression, when it grows does it just go to large size?

---

### Post by jdong on 2010-02-24
> **degarb said:**
> I am fuzzy on what happens to file sizes and readability when you mount/toggle compression. 

I seem to be thinking/assuming: if off, new files aren't compressed, when mounted on, then new files are written with compress but old files will be not be compressed.  Now if toggled off, are these compressed files readable and transparently working?  But what about files the a vdi that "grows"  if you create it in compressed drive, the turn off compression, when it grows does it just go to large size?


the **compress** option just means **new blocks (extents) written will be attempted for compression**.

Btrfs supports compression on a per-block (per-extent) basis so a file can be a mix of compressed and uncompressed components. So yes, your assumption is correct, if you have a large VM image that you created under compression AND btrfs felt the file was compressible (or you used -o compress_force), the file would be compressed at this point. Then, if you switch off compression, then the new changes to the file will be written uncompressed, and you end up with a mixture of compressed vs uncompressed.

---

### Post by degarb on 2010-02-24
> **jdong said:**
> Then, if you switch off compression, then the new changes to the file will be written uncompressed, and you end up with a mixture of compressed vs uncompressed.

Just to confirm.  a 'mixture'  within the file, itself!  This, if true, is great. 

Also, if I read right, there is no way to get an existing file in ext4 to compress to btrfs.  The convert will only convert, but I would need to move off drive and back on to compress it or do a file copy to new location.  It is a doubtful if a file move from one location on drive to another would do change to how the blocks are written in the file?


-----

Just to report back on my virtual machine install of windows 2000 on a 1.5 gig drive (compressed) that needs 2 gig to install.  It got to exactly same point as uncompressed drive before complaining it was out of space.  On an uncompressed drive the vdi (virtual drive image) was 1.5 gig.  On the compressed drive nautilus reported 1 gig and .5 gig free.  So, I assume I had the compression working correctly, but something was reporting to vbox that disk was full. I blame vbox.

---

### Post by degarb on 2010-02-24
Is there a command to convert a single file from compressed to uncompressed (and visa-vera), I missed?  This would be useful.  Buffet compression.

---

### Post by jdong on 2010-02-24
> **degarb said:**
> Just to confirm.  a 'mixture'  within the file, itself!  This, if true, is great. 

Also, if I read right, there is no way to get an existing file in ext4 to compress to btrfs.  The convert will only convert, but I would need to move off drive and back on to compress it or do a file copy to new location.  It is a doubtful if a file move from one location on drive to another would do change to how the blocks are written in the file?


A mixture within the file, correct.

> 

-----

Just to report back on my virtual machine install of windows 2000 on a 1.5 gig drive (compressed) that needs 2 gig to install.  It got to exactly same point as uncompressed drive before complaining it was out of space.  On an uncompressed drive the vdi (virtual drive image) was 1.5 gig.  On the compressed drive nautilus reported 1 gig and .5 gig free.  So, I assume I had the compression working correctly, but something was reporting to vbox that disk was full. I blame vbox.


Note btrfs's "df -h" output is deceptive because it does not account for how much space is being used by **metadata** -- the disk may become full far before df says it is full. This is especially true if you are using the default Karmic version of btrfs's kernel modules, or did the conversion using Karmic's btrfs.

> 
Is there a command to convert a single file from compressed to uncompressed (and visa-vera), I missed? This would be useful. Buffet compression


The way to do is is to trigger a rewrite of that file. You can either use "btrfsctl -d file" to do it atomically ("defragment") , or make a copy of the file, then rename the copy back to the original.

---

### Post by degarb on 2010-02-26
> **jdong said:**
> 
Note btrfs's "df -h" output is deceptive because it does not account for how much space is being used by **metadata** -- the disk may become full far before df says it is full. This is especially true if you are using the default Karmic version of btrfs's kernel modules, or did the conversion using Karmic's btrfs.


sudo apt-get install btrfs-tools
Yes, I am using karmic version.   I only see on btrfs-tools in repository.  How would I get a better version that would not have this metadata "bug".  

Will 10.4 have a newer version of btrfs?  Should I wait until then?

---

### Post by ibuclaw on 2010-02-26
> **degarb said:**
> sudo apt-get install btrfs-tools
Yes, I am using karmic version.   I only see on btrfs-tools in repository.  How would I get a better version that would not have this metadata "bug".  

Will 10.4 have a newer version of btrfs?  Should I wait until then?

I maintain a git snapshot of the last working version of btrfs on 2.6.31 kernel in my ppa:
Unmount the btrfs filesystem, and run:
```

sudo add-apt-repository ppa:ibuclaw/ppa 
sudo apt-get update
sudo apt-get install btrfs-tools btrfs-kernel-source

```

**If** you depend on the filesystem in the boot sequence of your system:
```
sudo update-initramfs -u -k all
```

When you remount the btrfs file system, I recommend running:
```
sudo btrfs-vol -b /path/of/mount
```
first.

Regards
Iain

---

### Post by jdong on 2010-02-27
Note that there are a few bugs in btrfs-vol -b that have non-mainline in-progress patches where it may get stuck in an infinite loop. Run it for a few hours, and if it doesn't finish, it's entirely safe to reboot the system.

---

### Post by bladerunner6 on 2010-03-12
im having issues at the update-grub part,
i am chrooting via USB install of lucid (2.6.32) and converting the internal lucid installation(2.6.33) to btrfs.

I do the patches, and replace the lines as you say like so
this patches fine so does running update-initramfs -u -k all
but when i do update-grub i get this error
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
my boot folder is on the same / partition.

---

### Post by ibuclaw on 2010-03-13
> **bladerunner6 said:**
> im having issues at the update-grub part,
i am chrooting via USB install of lucid (2.6.32) and converting the internal lucid installation(2.6.33) to btrfs.

I do the patches, and replace the lines as you say like so
this patches fine so does running update-initramfs -u -k all
but when i do update-grub i get this error
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
my boot folder is on the same / partition.

2 fatal mistakes here...

[LIST=1]
[*]You **must** have a separate partition for /boot - preferably ext2 - though ext3/ext4 will do just fine too.
[*]From the error, looks like you haven't mounted a /dev filesystem inside the chroot.
[/LIST]

Regards
Iain

---

### Post by bladerunner6 on 2010-03-13
how do i mount dev correctly?
also is it possible the patch doesnt work with grub 1.98?

---

### Post by ibuclaw on 2010-03-13
> **bladerunner6 said:**
> how do i mount dev correctly?
also is it possible the patch doesnt work with grub 1.98?

It's quite possible, yes.

You can check:
/usr/lib/grub/
/usr/sbin

for any files ending with **.rej**

Regards
Iain

---

### Post by wd5gnr on 2010-05-10
Great how to! I've wanted ZFS for a long time but hate to run my root under Fuse. This seems great -- put it on my netbook which is not critical to my everyday work flow. Compressed SSD! Fantastic.

However, one comment. After the chroot, I had no network connection in that shell. Turns out resolv.conf was not set up so I just went to a different shell that wasn't chrooted and said:

cp /etc/resolv.conf /mnt/etc/resolv.conf 

(as root, of course)

and then all was well (except for where I mistyped part of the patch change, but that's my fault)

Thanks again.

---

### Post by auzziedingo on 2010-05-14
Does this howto still apply to lucid 10.4??

---

### Post by wd5gnr on 2010-05-14
Worked for me on 10.4 32 bit Kbuntu Netbook remix.

Now to tell the truth -- I thought I would be smart and resize my ext4 to make the boot partition. For whatever reason it seemed to work and on a reboot cratered my root completely. Of course I was backed up and that's one reason I did it on the netbook, I can image it and restore it nothing flat. 

So then I actually did what the how to tells you to do and it worked fine.

---

### Post by MacUntu on 2010-05-16
Works fine with Lucid in a VM. I wasn't sure if converting would give me the real deal, so I cloned /, used mkfs.btrfs on /, and copied the files back from the clone.

---

### Post by ibuclaw on 2010-05-16
> **MacUntu said:**
> Works fine with Lucid in a VM. I wasn't sure if converting would give me the real deal, so I cloned /, used mkfs.btrfs on /, and copied the files back from the clone.

Converting does give you the real deal, and is currently the quicker way of getting yourself setup.

The alternative, using mkfs.btrfs, requires you to install Ubuntu from within Ubuntu using a debootstrap, or image clone.

---

### Post by MacUntu on 2010-05-16
I just remembered that converting ext3 to ext4 didn't convert existing files to use extents, so I played it safe. Oh well, wasted 15 minutes... :D

---

### Post by iggykoopa on 2010-05-27
just tried this on maverick too, they've already done most of what you need. Just install btrfs-tools and apply the grub patch and it works. For the compression I just tar'ed the whole partition onto an external drive then mkfs.btrfs and remounted, then copied the tar file back...only took a few minutes with the default install.

---

### Post by ibuclaw on 2010-05-27
> **iggykoopa said:**
> just tried this on maverick too, they've already done most of what you need. Just install btrfs-tools and apply the grub patch and it works. For the compression I just tar'ed the whole partition onto an external drive then mkfs.btrfs and remounted, then copied the tar file back...only took a few minutes with the default install.

Isn't the kernel version in Maverick 2.6.34 ?

If so, what you did to try to compress all data is not necessary. :)

See: [http://kernelnewbies.org/LinuxChanges#head-98c8fb9d359cfbdd4a10bdc0c9d2d168b4c9ebb3](http://kernelnewbies.org/LinuxChanges#head-98c8fb9d359cfbdd4a10bdc0c9d2d168b4c9ebb3)

Regards
Iain

---

### Post by wurststulle on 2010-05-28
> **bladerunner6 said:**
> 
but when i do update-grub i get this error
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).


i have the same error while update-grub but i think all is mounted:

```

root@ubuntu:/# mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

someone know why?

---

### Post by ibuclaw on 2010-05-29
> **wurststulle said:**
> i have the same error while update-grub but i think all is mounted:

```

root@ubuntu:/# mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)

```

someone know why?

This is a Btrfs File system thread. I suggest you raise a new support question for your problem.

---

### Post by wurststulle on 2010-05-29
> **ibuclaw said:**
> This is a Btrfs File system thread. I suggest you raise a new support question for your problem.

it occours while following your howto from page one. so i posted here...

---

### Post by ibuclaw on 2010-05-29
> **wurststulle said:**
> it occours while following your howto from page one. so i posted here...

OK, what part of the guide are you stuck on? What actions have you tried to do?

---

### Post by wurststulle on 2010-06-03
> **ibuclaw said:**
> OK, what part of the guide are you stuck on? What actions have you tried to do?

after chroot, editing fstab, applying grub patch and adding the three files i got:

```

root@ubuntu:/# update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
Cannot determine root device.  Trying legacy probe method
Cannot determine uuid of root device.  Trying legacy probe method
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.34-5-generic
Found initrd image: /boot/initrd.img-2.6.34-5-generic
Found memtest86+ image: /memtest86+.bin
done

```

---

### Post by ibuclaw on 2010-06-03
> **wurststulle said:**
> after chroot, editing fstab, applying grub patch and adding the three files i got:

```

root@ubuntu:/# update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
Cannot determine root device.  Trying legacy probe method
Cannot determine uuid of root device.  Trying legacy probe method
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.34-5-generic
Found initrd image: /boot/initrd.img-2.6.34-5-generic
Found memtest86+ image: /memtest86+.bin
done

```

That looks perfectly OK to me. Nothing out of the ordinary.

As grub-probe cannot stat() the btrfs file system, it falls back to legacy detection mode (what is supplied in the patch). If that fails, the update-grub process would die with an Error.

As it doesn't here, you are OK.

---

### Post by jfernyhough on 2010-06-07
An extra tip: if like me you wanted to test btrfs but didn't make a /boot partition to begin with (instead shrinking and repartitioning) you'll find update-grub doesn't find the kernel.

This is because it was previously installed to the / partition.

To fix: reinstall the kernel with /boot mounted.

This will save you an hour of WTF?@*!

---

### Post by nh2 on 2010-07-03
Is there a possibility to "clone" a full Btrfs tree (with subvolumes, snapshots and so on) online?

I think it should be possible the RAID-1 way:

[LIST=1]
[*]some device is mounted as /
[*]btrfs-vol -a backupdevice
[*]btrfs-vol -b   # clone data so its present on both devices
[*]btrfs-vol -d backupdevice
[*]now we have a full backup of / with all snapshots inside
[/LIST]

However, I'm not quite sure what -b does. The wiki says "balance chunks across all devices" which sounds rather like shifting data around instead of "cloning" it, as RAID-1 does.

Is there a way to perform such kind of ultimate Btrfs backup?

---

### Post by jpbrown on 2010-08-30
Awesome post.  I have just one question.  Has anyone figured out how to convert from ext4 to btrfs and convert the converted file system to RAID1 instead of RAID0?

btrfs-vol -a /dev/sdb5 /  would add a second device to the newly converted partition, but it does it as RAID0.

I've attempted to use dd and clone the entire disk and then use mkfs.btrfs -m raid1 -d raid1 against the second device's btrfs partition (which successfully wrote the file system wiping out all the content I cloned -- as one would expect).  But also as you might expect, the metadata on the second device is ignored as it is added to the first device.

I suppose I could try to:
1) clone the first disk (at least the partition tables & MBR)
2) mkfs.btrfs -m raid1 -d raid 1 /dev/sdb5 to set up raid1 on the secondary disk's btrfs partition
3) clone the data for the /boot and / partitions
4) mount the second device and change the UUID in the /etc/fstab
5) swap the drives around in the box so I'd be booting off the cloned device
6)  adjust the metadata on the new secondary disk (formerly the first disk) to have raid1
7) add the original drive into the btrfs file system with the btrfs-vol -a command

Not sure if this would work -- don't know what mkfs.btrfs really does when given the raid1 for -d & -m when 2 disks are specified instead of 1 disk.  This also is a lot of screwing around.

Anyone have another suggestion?

Edit 9/2/2010:  I can answer my own question.  The above doesn't work -- raid1 is apparently ignored when the filesystem is created with only one device.  I went through the process of moving reformatting one partition at a time, used rsync to transfer data as to not change the btrfs metadata and swapped drives around, verified that I was booting off the right devices and as soon as I added the second disk to the first and told btrfs to balance the data, instead of mirroring, it simply striped.

---

### Post by willu on 2010-10-23
Hi,
  I was using a raid1 zfs-fuse installation, and I wanted to move to btrfs.  I'm not using btrfs for /, but I wanted to move over without losing any data, even though my disks are full.  This should be possible because I was using raid1 - I can run in degraded mode during the switch.  The only problem is that mkfs.btrfs requires you to create the raid1 fs with at least two disks - you can't (yet) create an fs with 1 disk and add the second disk later. Here is what I did:


# get the size of the disk you want to move from (in 1k blocks)
cat /proc/partitions # look for /dev/sdb1
# create the large, sparse data file
dd if=/dev/zero of=large.img bs=1k count=1 seek=<size of disk in blocks>
# mount it on a loopback device
losetup /dev/loop0 large.img
# make the raid1 btrfs filesystem
mkfs.btrfs -m raid1 -d raid1 /dev/sdb1 /dev/loop0
# mount the filesystem once
mount -t btrfs /dev/sdb1 btrfs-mnt
# if that didn't work, try mounting it using /dev/loop0
# then unmount it again
umount btrfs-mnt
# undo the loopback setup
losetup -d /dev/loop0
# remove the sparse file
rm large.img
# mount the drive again in degraded mode
mount -t btrfs -odegraded /dev/sdb1 btrfs-mnt

# set up snapshots
# copy stuff onto the drive
# etc
cp -rp stuff btrfs-mnt/

# switch over /etc/default/zfs-fuse and /etc/fstab so the btrfs fs will be used
# remember that you're still needing to mount in degraded mode
# reboot

#add the second disk to the btrfs array
btrfs-vol -a /dev/sdc1 /data

#this is how things currently look:
btrfs-show
[INDENT]
failed to read /dev/sr0
Label: none  uuid: <snip>
	Total devices 3 FS bytes used 593.15GB
	devid    1 size 931.51GB used 931.51GB path /dev/sdb1
	devid    3 size 931.51GB used 0.00 path /dev/sdc1
	*** Some devices missing

Btrfs Btrfs v0.19
[/INDENT]
# rebalance the fs
btrfs-vol -b /data    # I'm currently in the middle of this, so from here on is speculative
# remove the missing volume (I did try this before the rebalance and had issues - we'll see if I still do after the balance...)
btrfs-vol -r missing /data

# modify /etc/fstab so that it no longer mounts in degraded mode
# reboot

Cheers,

Will         :-}

---

### Post by cerberos on 2010-11-11
> **ibuclaw said:**
> [COLOR="Sienna"][SIZE="3"]Offline file system check[/SIZE][/COLOR]
Self explanitory, really.
```
sudo btrfsck /dev/sda5
```
**NOTE**: btrfsck is **NOT** an online checker. **IT IS OFFLINE ONLY**, contrary to what the documentation said at one point. Running btrfsck online can lead to filesystem corruption! (thank-you for pointing this out jdong).

[COLOR="Sienna"][SIZE="3"]Online file system defragmentation[/SIZE][/COLOR]
Lastly, the feature everyone has been waiting for...
```
sudo btrfsctl -d /
```
The argument being the location of the subvolume you wish to defragment.
Quite boring, really. There is not even a progress bar. ;)


From reading the BTRFS mailing list this doesn't appear to be what the command actually does. All 
```
sudo btrfsctl -d /
```
will do is defrag the / folder, not any of the files under it.

There is also a lot of discussion that defragging files on a btrfs system will undo most of the advantages of COW gives.

---

### Post by mitcoes on 2010-11-17
I'm looking an easy way to format in btrfs a new hard drive in ubuntu for hosting my downloads.

It will be /media/M500, now is in NTFS with errors, and I abandoned MS WOS XP 6 months ago I almost copied all the information to my other ext4 partitions.

But Gparted do not allow me to format this disk in btrfs
An I did not find what to download to do it by console orders and add it to fstab if it is not automatically made.

I have seen Gparted versions (v7) that allows btrfs format, but I cannot find where to upgrade with a deb package, (mine is 0.6.2 Ubuntu 10.10, and the link from the program refers to the ISO Gparted disk image.

Thanks in advance for the upgrade, if it is possible, and for your previous work.

I am a semi-advanced user, I try to learn every day a little bit, but I like to do things in an easy way. If it is possible.

---

### Post by gimfred on 2011-01-09
Well, I don't know much about it all however, it seems to me that you could format in ext4 in gparted then upgrade the partition to btrfs.

look for 'upgrade ext3/4 to btrfs'

---

### Post by ibuclaw on 2011-01-10
> **gimfred said:**
> Well, I don't know much about it all however, it seems to me that you could format in ext4 in gparted then upgrade the partition to btrfs.

look for 'upgrade ext3/4 to btrfs'
That's what the guide does here (have you even read it?).

Though, as of Maverick/Natty, the Ubuntu installer offers the choice to use Btrfs file systems automatically. So you needn't go to the lengths you had to a year and a half ago.

---

### Post by dhillonv10 on 2012-04-29
Great tutorial! :popcorn:

Just wanted to let you know, this works just fine in Ubuntu 12.04 LTS: 

$ uname -r
3.2.0-23-generic-pae

As you know the installer now has the option to use btrfs by default, I picked the following setup: 

/boot 500 mgs and ext2, 
then / and /home were btrfs

Also the file-system checker has now been included in it.

---

