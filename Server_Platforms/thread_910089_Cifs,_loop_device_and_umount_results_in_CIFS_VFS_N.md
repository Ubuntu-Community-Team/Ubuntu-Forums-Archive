---
title: "Cifs, loop device and umount results in CIFS VFS: No writable handles for inode"
date: 2008-09-04
forum: Server Platforms
---

### Post by Thomaskj on 2008-09-04
Hi

//mounting
mount -t cifs -o credentials=/root/scripts/linkstation.cfg
//192.168.100.9/backup /mnt/linkstation

//setting up loop device
losetup /dev/loop0 /mnt/linkstation/driveimage

//mount the loop device in /mnt/backup
mount /dev/loop0 /mnt/backup

I can now write files to the mounted filesystem.

Then I unmount with:

//dismount
umount /mnt/backup

//remove loop
losetup -d /dev/loop0

//dismount
umount /mnt/linkstation

The problems:
-------
After the umount in dmesg and syslog I get:
CIFS VFS: No writable handles for inode
The amount of the errors depends on how much I have been writing to the loop device.
A simple mount and unmount gives 2 lines with the errors, if I have copied 500MB to the device it's multiple pages with the error.

Remark, the "No writable handles for inode" errors does first appear in syslog after umount.

Small files in the root and empty folders are gone next time I mount the loop device.
-------


The file driveimage file is created before first use after cifs mount with:
"
dd if=/dev/zero of=/mnt/linkstation/driveimage bs=1M count=1 seek=5000

losetup /dev/loop0 /mnt/linkstation/driveimage 

mkfs.ext3 /dev/loop0
"

I have tried with 5GB and the target is 350GB and eventually 1TB when we get a bigger NAS.


I have tried from two different distros as client.

Debian running 2.6.25-2-686 and CIFS Version 1.52
Ubuntu running 2.6.24-19-server and CIFS Version 1.52

Using two different servers:

One being a Bufalo Linkstation, running Samba 3.0.21c according to:
"cat /proc/fs/cifs/DebugData" when the linkstation is mounted.

The other is the above mentioned Debian running Samba 3.0.30.


The goal is to use a NAS as storage for an encrypted filesystem which is mounted when the backups needs to be updated.
mount -t cifs -o credentials=/root/scripts/linkstation.cfg //192.168.100.9/backup /mnt/linkstation
mount -o  loop,encryption=aes /mnt/linkstation/driveimage /mnt/backup -p0 < /root/scripts/loop.cfg

The encryption does not seem to influence if the errors are there or not.
Is it the cifs or is it the loop device which is causing the problems?




I have tried with the mount options forcedirectio and directio.

Those options does impact the performance of the mount, but does not avoid the problem.

All tests is on a LAN and I don't get the errors if I don't tunnel it through the loop device.

I suspect the "losetup -d /dev/loop0" don't end the loop device's connection to the driveimage file correctly.
It's the same if I use the loop integrated mount command:

"mount -o loop,encryption=aes /mnt/linkstation/driveimage /mnt/backup -p0 < 
/root/scripts/loop.cfg"

and then unmount with "umount /mnt/backup/"


Eventually, should I look for a totally different backup storage strategy?

It would be nice to know if you can replicate the error.

---

### Post by lmno149 on 2008-09-04
[swg credit](http://www.mybloglog.com/buzz/members/swg_credit/)[vanguard gold](http://www.mybloglog.com/buzz/members/vanguard_gold/)[wow gold](http://www.mybloglog.com/buzz/members/wow_gold/)[coh influence](http://www.myspace.com/coh_influence)[cov infamy](http://www.myspace.com/cov_infamy)

---

### Post by eightftcyborg on 2008-10-08
I am attempting nearly the same procedure.  The Samba server is a Debian installation.  However, I too run into this error.  I made the driveimage directly on the server, but I get the same errors you are encountering in the same fashion.  Have you found a solution to this?  Thanks.

---

### Post by Thomaskj on 2008-10-08
I did not get it to work with the loop device and cifs.

I gave up.

Instead I'm now using Truecrypt for the encryption layer.

Truecrypt can create/mount an encrypted filesystem inside a containerfile which you can place on a cifs / samba share.


My guess on why that it doen't work with the loop device and aes is that when you unmount the loop device it doesn't keep a busy flag on the cifs mount until it's done writing the changes.

I see that when I or the cronjob is done using the truecrypt container and dismount that, and right after tries to unmount the cifs share, the umount fails and says the device is busy.
The script then waits a few seconds, try unmounting again and if it also fails, it extends the delay.
Last resort is lazy unmount.

That does NOT happen with the loop device, which is why I think the reason to failure is somewhere close to that.

I have not tried with the lazy unmount in combination with the loop device. You can try that and report back.

Using lazy unmount is not great if you wanna remount again soon, as you don't know if it has unmounted automaticly yet. (There's probably a way to find out though.)


Please let me know what you end up with doing.

---

### Post by eightftcyborg on 2008-10-08
That's interesting.  I was getting the error even without unmounting the CIFS share, just from unmounting the loopback device.  I don't really need to unmount the samba share since the only thing in it is the encrypted diskimage.  I supposed I should, but I haven't gotten around to incorporating that into my backup script yet (which uses rsnapshot).

However, after poking around in a few places, I've found that using 'forcedirectio' in my cifs mount options for mounting the shared folder which contains the drive image file and then mounting the loopback device, followed by 'umount -d' when unmounting the loopback device seems to clear things up.  I wasn't including the -d option for the umount command before, but apparently it makes a difference in the subsequent mounts of the loopback device.  The mount command was still using /dev/loop0 every time, but something wasn't quite right.  I'll continue to play with this configuration and let you know if it indeed stable.

Thanks.

---

### Post by plogplog on 2009-01-28
The setup mentioned in the first post by Thomaskj can work. After getting the same error "CIFS VFS: No writable handles for inode", I investigated a bit more and found a way to solve it. In my case, the error occurred when detaching the loop device after having created a filesystem on it. I checked (with tshark -i eth1 -f "host ip.of.cifs.server") that indeed there was still traffic flowing to and from the server although the mkfs command had already returned. Just waiting for this traffic to actually finish before detaching the loop device solved the problem for me.


Regards, 

plogplog

PS: neither the client nor the server are ubuntu in my case, but since this page is high in the google results I chose to post this information here.

---

### Post by Thomaskj on 2009-01-28
> **plogplog said:**
> The setup mentioned in the first post by Thomaskj can work. After getting the same error "CIFS VFS: No writable handles for inode", I investigated a bit more and found a way to solve it. In my case, the error occurred when detaching the loop device after having created a filesystem on it. I checked (with tshark -i eth1 -f "host ip.of.cifs.server") that indeed there was still traffic flowing to and from the server although the mkfs command had already returned. Just waiting for this traffic to actually finish before detaching the loop device solved the problem for me.


Regards, 

plogplog

PS: neither the client nor the server are ubuntu in my case, but since this page is high in the google results I chose to post this information here.


Is it working on future unmounts?

I have tried the setup with completely different hardware and got the same result.

My solution to using a NAS as a container to store a linux filesystem is using Truecrypt and create an container with that.

The odd thing is that Truecrypt also relies on the loopdevice, but it doesn't allow the umount (device busy) before the writing to the NAS via CIFS is completed.

---

### Post by plogplog on 2009-01-31
It seems to work well on later unmounts. Adding the encrypted file to /etc/crypttab mounts it automatically as a loop device (so you don't have to mess around with losetup anymore) which contains a filesystem which you can mount as usual via a line in /etc/fstab. Trying to unmount this filesystem during a write fails with "device is busy" until the write has actually returned, so no problem.

Furhermore, trying to delete the loop device while the filesystem is still mounted fails with "ioctl: LOOP_CLR_FD: Device or resource busy". 

So you can't unmount the filesystem while it is in use, and you can't delete the loop device while the filesystem is mounted. 

Regards, 

plogplog

---

