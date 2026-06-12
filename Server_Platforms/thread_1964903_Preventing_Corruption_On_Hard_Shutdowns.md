---
title: "Preventing Corruption On Hard Shutdowns"
date: 2012-04-24
forum: Server Platforms
---

### Post by Spaceman Spiff on 2012-04-24
Hello all,
  I am using Ubuntu 10.04 LTS, to run a small "server" type application on a larger system.  The larger system is powered down when not in use.  This power down, translates to my onboard computer being shutdown through power removal (instead of a typical shutdown -P call.)

  I would like to ensure that my computer continuously boots Ubuntu without any corruption.  Once my application is finished and running, nothing will need to be added/written to the hard drive.  This leads me to look to maintaining the hard drive as read-only.

  However, I have read that I cannot boot from a read-only file system.  My google bubble has been exhausted and my searches are not returning how to implement my approach.  Could anyone offer any suggestions/articles/search terms on how to set up my ubuntu to boot read-only and never write to the hard drive.

Thank you in advance,
Constantin

---

### Post by kevinthecomputerguy on 2012-04-24
Dont use a hard drive, and instead use the ubuntu live cd.

---

### Post by Spaceman Spiff on 2012-04-25
Hey kevin, thank you for your response.  Unfortunately, I cannot take that approach.

However, I think I have stumbled on a possible solution.  I am going to mount the entire filesystem as readonly, then use tmpfs to mount the necessary /var folders.

Could anyone offer any advice if they've done this?  All the information I've found is outdated, relating to ubuntu 9.04.  Am I in the correct section, this seems to be very server oriented.  Thank you.

---

### Post by SeijiSensei on 2012-04-25
Corruption after a power outage only affects open files.  If you're willing to put those files in tmpfs, then it sounds like you don't need to have them persist across reboots anyway. In that case I wouldn't worry.  If you are going to mount /var on a separate filesystem, I'd choose a USB key over tmpfs.  Or if you do use tmpfs, I'd suggest running an rsync job out of cron every few minutes and writing the files you need to keep to a USB key.

---

### Post by Spaceman Spiff on 2012-04-25
Hi Seiji, you are correct, nothing needs to be written/saved.  I am not doing any type of logging.  I am attempting to prevent corruption on the filesystem/harddrive itself.  I need it to load EXACTLY the same EVERY time.

I am confused on how to set up my system to do this correctly though.  I was hoping someone would have a tutorial.  I am setting up a test os on my VM right now to spend the day figuring out how to set it up as read-only.

So tmpfs is the correct approach?  I am not running GDM on my 10.04, so free return 1.9 gigs available.  Is tmpfs using my ram?  Or my swap?  Can I use my swap instead?  That's already a writable partition.

---

### Post by Jonathan L on 2012-04-25
Hi Spaceman Spiff

> I am going to mount the entire filesystem as readonly, then use tmpfs to mount the necessary /var folders.

Could anyone offer any advice if they've done this?  All the information I've found is outdated, relating to ubuntu 9.04.

I do exactly what you're describing, in two production setups, both running 10.04 Desktop, and various experimentals running server images.

1.  File server with RAID stays on all the time.  Diskless compute servers boot via PXE from the file server.  As they don't have any disks, doesn't matter when they go off.  They read and write files only to /dev/shm.  They are turned on and off by a remote-control power switch, driven by the file server on cron.

2.  Sound studio workstation with much RAM boots a lightly modified 10.04 Desktop Live CD image on USB flash stick, where everything is read-only, only making files in /dev/shm and similar.  No disk = no problem.  Also, incidentally, very quick, as everything is already in RAM.

I'm afraid I don't know of any canned installation for doing either of these (except the Live CD) but will be happy to give tips from my runing systems if that helps.

The place to start is the init script inside /boot/initrd.img-VERSION to see what options you've got.  Let us know exactly what version you're wanting to use and we can give more detailed advice.

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by Spaceman Spiff on 2012-04-25
Hey Jonathon thank you for the support offer!

I am running 10.04, I believe the 2.6.34 kernel.  I don't have the system with me right now ... and I just blew away my test VM with some bad settings (rage face).

Jonathon, could you tell me what folders you mounted as write?  I plan to disable the following systems:
  1) xserver (and gdm)
  2) cups

Maybe more as I figure out what I don't need.

Also where does tmpfs physically mount these folders?  Does it create a "ramdisk" overlay?  Where did you do the calls to mount them?  The article I'm reading suggests to do the mount calls inside:  /etc/init.d/mountkernfs.sh

---

### Post by Jonathan L on 2012-04-25
> I am running 10.04, I believe the 2.6.34 kernel.

Hi ... Did you want server or desktop? ... and I'll guess 10.04.4?

Kind regards,
Jonath_**a**_n.

---

### Post by Spaceman Spiff on 2012-04-25
Jonathon, I apologize.  I am using 10.04.4, the desktop version.

Regards,
Constantin

---

### Post by Jonathan L on 2012-04-25
> 10.04.4, the desktop version.

... and want to boot from local hard disk, correct?  PXE diskless from the big server is out of the question?  (You'd need to run DHCP/TFTP/NFS on that.)

... just checking so I give you appropriate notes.

Kind regards,
Jonath_**a**_n.

---

### Post by Spaceman Spiff on 2012-04-25
Correct, I am booting from a local hard disk, it's setup with a 2 gig swap, and a single ext4 partition, mounting /

---

### Post by SeijiSensei on 2012-04-25
First off, you need to determine which files are malleable and where they are located.  Sounds to me like you think the app is writing to some part of /var. If so, you'd just edit /etc/fstab to mount /var to a different filesystem than the root, either a ramdisk using tmpfs or, as I suggested above, a USB pendrive.

There are two questions you need to answer empirically.

1) What files does the application create?

One good solution to this is to use rsync to back up the entire root filesystem to an external device.  Then let the system run for a day or two and run rsync again.  If you use "rsync -av source target" you'll get a list of all the files that rsync has determined have changed since the initial backup.  If they're all under /var, you're a long way down the road.

2) How big a filesystem do I need?

The simplest answer to that is to run

```
cd /
sudo du -s var

```

and see how big /var is.  On my desktop machine /var/tmp and /var/cache are fairly large, but much of tmp is KDE-related, which won't exist on a server.  /var/cache includes /var/cache/apt/archives which has copies of all the update debs you have installed.  Since you don't intend to update the system, that shouldn't be an issue for you.

---

### Post by Jonathan L on 2012-04-27
Hi Spaceman Spiff

> booting from a local hard diskI had a little time last night and tested the following for 10.04.4 Desktop, for readonly systems based on the Live CD.  It is not the most flexible method for booting but all of the hard work for using a readonly-system has been done, and because it's based on the stock CD, it's very reliable.  As I say, I use this in production for several systems which are switched on and off by power cycle (although those systems use PXE booting).

Basically what you do is put the contents of the Live CD on a partition, but boot from grub rather than isolinux (or pxeboot).  I made a small partituion of 4 Gbyte as the nominal CDROM, and remainder of disk for a second partition, for data or whatever.

I did the following by booting over a network.  You could boot over a real CD-ROM or put the disk into a working computer.  I tested on HP DL320 G2 server hardware with 2 Gbyte RAM + 1 x 40 Gbyte disk

If it's not obvious: the following will destroy any data on your disk: only do it if you're sure you want to

```
# partition the disk
# delete existing, make new  on partition 1 (+4G), and partition 2 (defaults)
sudo fdisk -uc /dev/sda

# format those
sudo mkfs.ext3 /dev/sda1
sudo mkfs.ext3 /dev/sda2

# mount them for setup
mkdir /tmp/1
mkdir /tmp/2
sudo mount /dev/sda1 /tmp/1
sudo mount /dev/sda2 /tmp/2

# get the cdrom image, mount it, copy it
cd /tmp
wget wget http://releases.ubuntu.com/releases/10.04.4/ubuntu-10.04.4-desktop-i386.iso
sudo mount -o loop ubuntu-10.04.4-desktop-i386.iso /cdrom
# note careful copying to ensure we get everything include .disk
cd /cdrom
sudo cp -Rp . /tmp/1

# put grub boot loader on
sudo grub-install --root-directory=/tmp/1 /dev/sda

# make boot config file
cat << //// > /tmp/grub.cfg
root (hd0,1)
linux /casper/vmlinuz root=/dev/sda1 boot=casper
initrd /casper/initrd.lz
boot
////

# copy to right place
sudo cp /tmp/grub.cfg /tmp/1/boot/grub/grub.cfg
```This boots straight up into the desktop, with everything readonly.  You'll have to fool around with settings to strip things out, if you care, or to customise, but this should get you going.

Basically you get a union file system of your "CDROM" and the contents of a squashed filesystem  which is in /casper/filesystem.squashfs.  You can unsquash that and make lots of changes; also obviously remove lots of things from the CDROM image if you don't want them.

Hope that's helpful

Kind regards,
Jonathan.

---

### Post by Jonathan L on 2012-04-27
> You can unsquash that and make lots of changesJust for completeness I thought I'd add this

The system boots the initial ram disk from the initrd.lz file, which is a compressed cpio archive.  This has got the initial drivers and the critical startup file 'init'.  Because we chose 'boot=casper', we'll run scripts/casper to get things going, which mounts a new root from $root/casper/filesystem.squashfs, and as we specify root=/dev/sda1 in the kernel flags, we'll get /dev/sda1/casper/filesystem.squashfs mounted.  This contains the real /etc with fstab, rc.local and so on.  To customis, you might mount a second partition, probably readonly, and run a script on it from /etc/init.d or /etc/rc.local or wherever.

As described in my previous post, we have /dev/sda1 mounted on /cdrom readonly.  To modify, we remount read-write:
```
sudo mount -o remount,rw /dev/sda1

```To modify the squashed filesystem:
```
# get tools if you don't have them
sudo apt-get install -y squashfs-tools

# unpack
cd /casper
sudo unsquashfs filesystem.squashfs
cd squashfs.root

# fiddle in etc or wherever

# repack
cd /casper
sudo mksquashfs squashfs-root filesystem.squashfs

```If you need to fiddle around with initrd.lz
```
# unpack
sudo mkdir /tmp/newroot
cd /tmp/newroot
lzcat -S .lz /casper/initrd.lz | sudo cpio -i

# repack
cd /tmp/newroot
sudo sh -c "find . | cpio --dereference -o -H newc | lzma -9 > /casper/initrd.lz"
```Hope that's helpful for someone.

Kind regards,
Jonathan.

---

### Post by Spaceman Spiff on 2012-04-28
Jonathan, thank you so much for the information!!  I have been offsite working an on a project and have been unable to respond.

This is a very well documented and interesting approach.

To answer your earlier question, nothing of mine is writing to /var .  Perhaps the only thing writing to /var would be the system log.  Nonetheless, I have determined a working solution, could you critique it for me?

I went to my fstab, and simply set the mount option for "/" as ro.  My computer still boots fine and the entire filesystem is read only.  Would you happen to have any thoughts on that?

Also have you done this process with ext3?  I have installed a variety of necessary libraries and set this computer up for its purpose.  If this was on my own time, I would sit down, take a few days and get it right.  However, in my circumstances, I do not have the time to reinstall/resetup the system.  I would like to make the system read only, using its current state.

A note about tmpfs.  I blew away a few VM's, I could not get my /var to mount as a tmpfs....  My fstab entry's were something along the lines of (I don't have them with me right now)

ID_BLABLA   /      ext4       ro,exec,noatime, 0 0

/var        /var   tmpfs      remount,rw 0 0

---

### Post by Jonathan L on 2012-04-29
Hi again

> nothing of mine is writing to /var .  Perhaps the only thing  writing to /var would be the system log.  Nonetheless, I have determined  a working solution, could you critique it for me?

I went to my fstab, and simply set the mount option for "/" as ro.  My  computer still boots fine and the entire filesystem is read only.  Would  you happen to have any thoughts on that?

Also have you done this process with ext3?

A note about tmpfs.  I blew away a few VM's, I could not get my /var to  mount as a tmpfs....  My fstab entry's were something along the lines of  (I don't have them with me right now)

ID_BLABLA   /      ext4       ro,exec,noatime, 0 0

/var        /var   tmpfs      remount,rw 0 0I'm a huge fan of various kinds of reduced system, from the completely diskless, readonly disks, "dataless" (an old Sun term for local system and swap, NFS-mounted data) and so on.

If I want to protect against data loss due to power cuts (intentional or otherwise), I normally try to have no disk writing at all, including swap.  If swap is a requirement, it's best on a physically separate disk.

If I've got storage which will only be read, I prefer if it simply cannot be written.  For this reason I'm a fan of CD-ROMs, compact flash cards with write-protect switch and so on.  I've even used disks where I've disconnected the "write-enable" signal!

For logs on readonly machines it's good to redirect them (via rsyslog config) to something, perhaps your big server is suitable for this.

What you've got doesn't look quite right.  /var should be either a ramdisk (if you don't need any non-volatile storage at all) or at the very least a separate partition.  If you remount a portion of a readonly filesystem as read-write, you are really writing into the underlying, parent, filesystem.  But the basic scheme is correct: /var contains variable things, and is essentially the conventional setup since /var was introduced: everything readonly except /var, which might be a ramdisk, and perhaps /home, which might be nfs mounted.

So I'd suggest jigging your partiions a little and getting a separate one for /var, mounted rw.

It should make no any difference which kind of filesystem you use, ext3, ext4, ufs.  (indeed if you have a journalling or soft-update type file system or suitable RAID, there's an argument that you hardly need worry about any of this: just let it crash and fix itself!  I don't recommend it in general, but it _is_ worth considering for special cases.) 

If you're curious, I use a slight modification of the Live CD scheme I described earlier, where the one change is that /etc/rc.local uses wget to pull a script from a central place and run it.  So my computers in that installation all are the same up to the point where they pull their "differentiation" script.  Brutal but effective and very reliable.  (They then pull any required .deb and install them and go from there.)

Hope that's of some use.

Let us know how you get on.

Kind regards,
Jonathan.

---

### Post by Spaceman Spiff on 2012-04-29
Jonathon, this is great information!  Cute idea with the wget script.

Let me see if I understand correctly.  I can just make a tmpfs partition that is mounted to memory at boot with /var?  I have 2 gigs, I only use < 500 megs of it!  I outline the procedure as I understand from your description below:
[LIST=1]
[*] Create tmpfs partition (would this be in an init script?) (or should I specifically google how to make ramdisk partition)
[*] mount / to main hd as ro
[*] mount /var to the tmpfs partition (is this in the fstab?) as rw
[/LIST]

Is this the process you are describing or am I misunderstanding?  If so, I really like this process, as it doesn't require me to re-setup my OS configuration and installed libraries.

---

### Post by Jonathan L on 2012-04-29
> Let me see if I understand correctly.  I can just make a tmpfs partition that is mounted to memory at boot with /var?  I have 2 gigs, I only use < 500 megs of it!  I outline the procedure as I understand from your description below:
[LIST=1]
[*] Create tmpfs partition (would this be in an init script?) (or should I specifically google how to make ramdisk partition)
[*] mount / to main hd as ro
[*] mount /var to the tmpfs partition (is this in the fstab?) as rw
[/LIST]
 Is this the process you are describing or am I misunderstanding?  If so, I really like this process, as it doesn't require me to re-setup my OS configuration and installed libraries.

Hi Spaceman

Yes, that's exactly it.  (I only use "ramdisk" as it's a kind of generic word, in Linux systems yes, that means "tmpfs".)

I not sure of the exact details but I think you make /var simply in /etc/fstab, and /etc/init/mouned-varrun.conf does the rest.

Hope that helps.  I should be able to give it a test tomorrow.

Kind regards,
Jonathan.

---

