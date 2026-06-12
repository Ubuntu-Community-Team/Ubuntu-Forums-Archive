---
title: "Copy Ubuntu Server 8.04 LTS from IDE Hard Drive To USB Drive"
date: 2008-10-16
forum: Server Platforms
---

### Post by wbelk7777 on 2008-10-16
I have installed Ubuntu Server 8.04 LTS on an IDE hard drive.  I have setup samba on the server.  I would like to transfer the operating system to a USB thumb drive so that I can boot and run the same computer from the thumb drive and get rid of the IDE Hard Drive.  What is the easiest way to do this?  Thanks.

---

### Post by Krupski on 2008-10-16
> **wbelk7777 said:**
> I have installed Ubuntu Server 8.04 LTS on an IDE hard drive.  I have setup samba on the server.  I would like to transfer the operating system to a USB thumb drive so that I can boot and run the same computer from the thumb drive and get rid of the IDE Hard Drive.  What is the easiest way to do this?  Thanks.

Use the "dd" command.

First, boot up your Ubuntu system and plug in your USB drive.

Next, find out what the device names are:


```

sudo ls -laF /dev/disk/by-id

```

Figure out which device is your Ubuntu drive and which is your USB drive.

Hopefully, both drives are the same size? If not, the partition table mismatch will give you grief.

Next, copy one to the other. Note that in the following example, I will use "/dev/sda" as the Ubuntu drive and "/dev/sdb" as the USB drive. [COLOR="Red"]**These are EXAMPLES, you MUST use the proper device names that YOU figured out.**[/COLOR]

```

[COLOR="Red"]**# WARNING - EXAMPLE ONLY - DO NOT EXECUTE**[/COLOR]
sudo dd if=/dev/sda of=/dev/sdb

```

The line means "super user do dd input file=/dev/sda and output file = /dev/sdb and copy all of it.

This will copy every byte from your Ubuntu drive to the USB drive. Assuming that your computer supports booting from a USB drive, you should then simply be able to plug in the USB drive and boot into it.

Please though... be VERY careful that you use the proper device names. If you get it wrong, you could irretrievably wipe out important data.

Good luck!

-- Roger

---

### Post by prosonik on 2008-10-16
Hi, 

I was playing around with something similar last night. I installed 8.10 to a flash device, and and wanted to copy it to larger drive. I don't know if this will work for hardy or ide, but i used dd..

```
#sudo dd if=/dev/sdb of=/dev/sdc conv=noerror,sync bs=4k
```

/dev/sdb was the orginal drive, /dev/sdc was the new drive.

i used 

```
#sudo fdisk -l
``` to check to see what the drive names where.

hope this helps,

pro

---

### Post by wbelk7777 on 2008-10-16
Thanks for the replies.  

Krupski, 

I know that there will be a size difference between the IDE and USB drives.  The IDE drive is 20GB, but only about 2GBs is used.  The USB drive is 8GB.  How can I resolve the partition issues?

Prosonik,
What does conv=noerror,sync bs=4k do?

Thank you for your help.

---

### Post by C.S.Cameron on 2008-10-17
After backing up your data you can use gparted to shrink your server partition down to less than 8G and then clone it using dd.

---

### Post by cariboo on 2008-10-17
You can also use partimage, it works the same way as dd but does not duplicate the empty space. Partimage is available in the repositories.

Jim

---

### Post by alienprdkt on 2008-10-17
here's how I backup all my hard drives, hope it helps out.

BACKUP YOUR MBR
    You should do this before you edit your partition table so that you can put it back if you mess things up.

    # dd if=/dev/hda of=/root/hda.boot.mbr bs=512 count=1
    If things mess up, you can boot with Knoppix, mount the partition containing /root (hda1 in this example) and put back the MBR with the command:
    # dd if=/mnt/hda1/root/hda.boot.mbr of=/dev/hda bs=512 count=1 


     Getting around file size limitations using split  

    When making images, it's quite easy to run up against various file size limitations. One way to work around a given file size limitation is to use the split command.

# dd if=/dev/hda3 | gzip -c | split -b 2000m - /YAGI/backup.img.gz

Then whenever you need to restore your USB stick to the Gentoo Live image you built, you can run a command like the following:

To restore the multi-file backup, do the following:
# cat /mnt/hdc1/backup.img.gz.* | gzip -dc | dd of=/dev/hda3

1. Cat recombines contents of the compressed and split image files to stdout, in order.
2. Results are piped through gzip for decompression.
3. And are then written to the first partition of the hard drive with dd.

---

### Post by promodus on 2008-10-18
Some of you guys do things the hard way.
dd is overkill.

Create the partition on your usb drive.
format it:
mkfs.ext3 /dev/sd*

Copy your files over

cp -ax source destination

Replace UUID in FSTAB and in GRUB

---

### Post by prosonik on 2008-10-19
Hi there,

Here is an article on using DD to restore a crashed drive. The author goes step-by-step to explain each switch he using, including the one i have used. 

[http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-dd.html]("http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-dd.html")

As with everything, there seems to be multiple paths to the same destination.. 

pro


> **wbelk7777 said:**
> Thanks for the replies.  

Prosonik,
What does conv=noerror,sync bs=4k do?



---

### Post by prosonik on 2008-10-19
interesting. 
using cp, will you be able to boot from the drive? what about the mbr.

pro



> **promodus said:**
> Some of you guys do things the hard way.
dd is overkill.

Create the partition on your usb drive.
format it:
mkfs.ext3 /dev/sd*

Copy your files over

cp -ax source destination

Replace UUID in FSTAB and in GRUB

---

### Post by rcrcomputing on 2008-10-19
I'd skip the mbr, grub, uuid, problems and do an rsync. Here's the script I use for a hot clone using rsynce_backup_restore.sh. You can read the quick-notes and get the idea..

[http://programs.rcrnet.net/](http://programs.rcrnet.net/)

On source machine:
Download script
chmod 755 rsync_backup_local.sh
Edit the top of the script with your values
Run the rsync_backup_local script.sh on the source machine
Shutdown services like mysql and postfix etc.. (Alternatively do a mysql dump)
Run it again (runs really fast this time)

On target machine:
Install a base system with a "alternate cd" on the new machine
At boot, type in "cli" this will choose no software, and finish the installation.
Edit rsync_restore_local to your values
Run the rsync_restore_local script.sh on the new machine
When done reboot the machine. It's that easy..

---

