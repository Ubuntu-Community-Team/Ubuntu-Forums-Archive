---
title: "replacing a LUKS encrypted drive"
date: 2012-03-21
forum: Security
---

### Post by strysnie on 2012-03-21
I tried many searches on this and I'm just not hitting the right combination of search terms...

Can anyone point me to a procedure for replacing a LUKS encrypted drive?  I have a laptop with 11.10 installed using the alternate install and full disk encryption.  I would like to replace the drive via some type of backup/restore procedure to preserve the current system contents and configuration.

---

### Post by strysnie on 2012-03-22
I found all of the info I needed but it was spread across multiple sources.  Below is the procedure I used, hopefully this will be helpful to others in the future.

These are instructions for upgrading the disk drive in a machine that was installed using the alternate install and asking for LUKS encryption of the entire drive.  These instructions assume upgrading from and old drive that I will refer to as "hd" to a new drive that I will refer to as "ssd" (since that's what I did - upgraded from a laptop hard drive to a solid state drive.)  Also assumed is creating pretty much an exact replica of the existing install.  If you want to upgrade to a new OS version that should be done before or after this process.

First install only the ssd in machine.  Install Ubuntu from CD using same options (machine name, user name, time zone, etc.) as old install.  This gives you a new install that should be similar enough to your old install that we can simply copy all files from the root partition of the hd to the root partition of the ssd and have an operational system.  This approach eliminates having to define partitions, volume groups, volumes.  If you know what you are doing it would be quicker to just create that stuff manually but doing a new install makes the process less prone to errors.

Shutdown, boot from the ssd, and copy the installed /etc/fstab and /etc/crypttab for future reference:
sudo cp /etc/fstab /etc/fstab.install
sudo cp /etc/crypttab /etc/crypttab.install

Shutdown, remove ssd, reinstall hd.

Boot from CD, choose "try Ubuntu".

Open a terminal and switch to root:
sudo su -

Install lvm tools:
apt-get install lvm2

List drives:
fdisk -l

Decrypt encrypted volumes:
cryptsetup luksOpen /dev/<device> <choose a name>

Scan for volume groups and list:
vgscan
vgs

By default the new install will have assigned the same volume group name as the old install did and we will not be able to work with two volume groups with the same name.  Change the volume group name on the hd:
vgrename <oldname> <newname>

Attach the ssd via USB.

List drives:
fdisk -l

Decrypt encrypted volumes on ssd:
cryptsetup luksOpen /dev/<device> <choose a name>

Make all volume groups active:
vgchange -ay

List volumes:
lvs

Create mount points:
mkdir /mnt/ssd
mkdir /mnt/hd

Mount volumes:
mount /dev/<vg name on ssd>/root /dev/ssd
mount /dev/<vg name on hd>/root /dev/hd

Go to the mount points and look around to make sure you are seeing files on old and new drives as expected.

Copy files from hd to ssd.  The options I uese are:
-P do not follow symbolic links in SOURCE
-p preserve mode, ownership, timestamps
-r copy directories recursively
-v verbose

cp -Pprv /mnt/hd/* /mnt/ssd

Now as part of the above command /etc/fstab and /etc/crypttab were copied and they will have the UUIDs of the hd in them.  This is why we saved copies of those files earlier.   Edit these files and substitute the UUIDs of the ssd which you will find in the saved files.

Shutdown, remove hd, install ssd, boot.  

That's it, hopefully everything works. "It worked for me." ;)

---

### Post by Cheesemill on 2012-03-23
Or you could just dd the old drive to the new one.

---

### Post by strysnie on 2012-03-23
I had read about dd but saw several posts saying that that it will not work with encrypted vgs/volumes.  Encrypted filesystems seemed to be no problem.  If you know that it will work please do tell how, it would save a lot of time over the procedure I posted above.

---

