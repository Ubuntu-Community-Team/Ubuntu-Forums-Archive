---
title: "External HDD /etc/fstab NOT MOUNTING AT BOOT"
date: 2008-12-25
forum: Server Platforms
---

### Post by crypticlabs on 2008-12-25
Hello,

I have recently installed Ubuntu 8.10, updated it, and then installed nfs-kernel-server and portmap.

I then modified my /etc/fstab file to mount my external HDD (Western Digital, 1TB) at boot. I used the following command to see which device to use:

fdisk -l

Which returned this:

/dev/sdb1

My /etc/fstab file looks like this:

/dev/sdb1	/media/STORAGE	ext3	rw,nosuid,nodev,uhelper=hal	0	0

I can mount the HDD by issuing the following command:

mount  -a

Which I understand to mount all filesystems in fstab. And this works, no problem. The issue I am running into is when I reboot the server, when drives are being mounted, there is the following message:

* Mounting local filesystems...
mount: special device /dev/sdb1 does not exist.

When the OS has started, fdisk -l says that the HDD is at /dev/sdb1 and if I issue mount -a, the HDD mounts. This is particularly a problem for me because I share this disk using NFS. NFS then complains that the shares I setup in /etc/exports don't exist.

This isn't too much of a problem as I don't plan on rebooting the server often but it shouldn't be happening, the HDD should be mounting automatically.

Any thoughts?

Thank you.

---

### Post by gtdaqua on 2008-12-26
May be the mountfilesystem script runs before the /dev/sdb1 is initilized. You could add the line "mount -a" in /etc/rc.local file which would mount all drives just before showing the login prompt.

---

### Post by crypticlabs on 2008-12-26
***UPDATE***

I decided to reinstall Ubuntu 8.10 Server and use the installation partition utility to reformat the external USB HDD. I configured it to be EXT3 and mount at /media/STORAGE. Upon reboot, I found the same thing happened. Startup complained that /dev/sdb1 didn't exist but when the system started, I could issue 'mount -a' and the HDD would mount.

Here is where it gets strange: By accident, I found that if there is a CDROM in the computer upon starting it, the external USB HDD gets mounted on startup. I no longer have to issue the 'mount -a' command after the system starts up. This sounds like a bug...Any thoughts?

If this does sound like a bug, how to I go about filing this? Also, I'm going to try Ubuntu 8.04 LTS Server to see if there is this behavior. FYI, I know this isn't normal, this computer was running CentOS 5.2 and I had the same setup and was not experiencing this issue. This isn't a deal breaker and I'm going to stay with Ubuntu Server, but I thought it was worth mentioning. 

Thank you.

---

### Post by crypticlabs on 2008-12-26
Ok, I just tried Ubuntu 8.04 Server (that installed FAST)...the issue did not seem to be there. The external USB HDD was mounted automatically upon starting up and there didn't have to be a CDROM in the computer.

I'm not sure if it's worth it to me to stay with 8.04 just for this or not, like I had said earlier, I'm not rebooting this computer often anyway and when I have to, it is very easy to mount the drive manually.

---

### Post by fjgaude on 2008-12-26
You might find the UUID of the partition and use that in the **fstab**. Works for me and others... **blkid** works fine for finding UUIDs.

```
UUID=xxxxxyyyyzzzzzzzz /media/STORAGE ext3 rw,nosuid,nodev,uhelper=hal 0 0
```

After /dev/sdb1 is mounted, what does the **mtab** file show for it?

---

### Post by crypticlabs on 2008-12-26
fjgaude - 

Well, right now I still have Ubuntu 8.04 installed and the mtab shows:

/dev/sdb1 /media/STORAGE ext3 rw,relatime 0 0

But when I reinstalled Ubuntu 8.10 and reformatted the HDD with the install partition utility (which I hadn't done when I first installed 8.10), it setup /etc/fstab for me and included UUID but made no difference.

---

### Post by fjgaude on 2008-12-26
Okay, I think you might have a "race" condition. Edit this file:

**/usr/share/initramfs-tools/init**   # to stop a race condition

```
   187 maybe_break mount
   188 sleep 10
   189 log_begin_msg "Mounting root file system..."
```

```
sudo /usr/sbin/update-initramfs -uk all
```    # run to rebuild the image

Make sure you get to the "mount" line. Lines numbers are likely different for your setup than mine.

If this works you might try lower number than 10 to get the least delay needed. If it doesn't some other delay could be added, here and there.

Good luck!

---

### Post by richwils on 2009-04-28
> **fjgaude said:**
> 

If this works you might try lower number than 10 to get the least delay needed. If it doesn't some other delay could be added, here and there.

Good luck!

Didn't work with a value of 10, but did with 15.

Many thanks.

Rich

PS.  I have reported this as a bug on Launchpad.

---

