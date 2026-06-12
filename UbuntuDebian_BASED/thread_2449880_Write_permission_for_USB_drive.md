---
title: "Write permission for USB drive"
date: 2020-09-03
forum: Ubuntu/Debian BASED
---

### Post by larryb1607 on 2020-09-03
Using a distro based on Ubuntu 18.04.  I recently formatted a USB drive in EXT4.  I am using it for Timeshift and backing up other files that I wish to reuse when I upgrade to version.  I am however unable to write to any of the available space on this drive.  Ut looks like I need to configure the drive so I can write to it, but checking around online, I cannot find any information that is at my ability level.  The drive is SDG2 and I have the UUID, have not been able to get past that point.  Is there something I can do during the formatting that would give me write permission?  Otherwise, what do I need to do.  Cannot understand why the system takes ownership of this as it is my drive.

Thanks

---

### Post by CelticWarrior on 2020-09-03
You can chown it or, likely simpler, format it with Disks.

---

### Post by TheFu on 2020-09-03
Is the storage mounted?  That doesn't happen automatically.  Normally, we use fstab to mount partitions for permanent storage.
After mounted, use **chown** to control the owner of the mounted directory.  ext4 is a fine file system for this purpose.

Usually backups need to be made using the root account.  Access that with sudo, but doing it for GUI programs is a bad idea due to unwanted side effects.  Without root/sudo, important file metadata will be lost.  Linux is a multi-user system.  Different accounts are part of the way the OS works.  Backups need to handle that aspect.

I don't know anything about that backup program but other tools work fine.  There should be a guide for using sudo safely with it.

---

### Post by coffeecat on 2020-09-04
> **larryb1607 said:**
> Using a distro based on Ubuntu 18.04. 

*Thread moved to **Ubuntu/Debian based** sub-forum.*

---

### Post by The Cog on 2020-09-04
I would change the permissions on the mounted drive so that all users can write to it. Assuming it mounts at /media/username/drive name, then 
sudo chmod 777 /media/username/drive name
Should do it. I would put code tags on that second line but it seems impossible with this tablet.

---

### Post by SeijiSensei on 2020-09-04
deleted ; see below

---

### Post by SeijiSensei on 2020-09-04
Mount the device to a known location via /etc/fstab. For instance, my 4 TB outboard USB drive that I use for backups has this entry in /etc/fstab:

```
UUID=62bc0cab-e5e7-4bb3-9500-79e7e666ee27 /media/external  ext4   defaults 0 0
```

I created the mount point /media/external with "sudo mkdir /media/external" before mounting the device.

Usually you want to run backups as the root user, but I know nothing about Timeshift. If it's running under your username, then you would want to own the entire filesystem:
```
sudo chown username:username -R /media/external
```
should give "username" write privileges on the mounted filesystem.  If you still get denials, run
```
sudo chmod u+w -R /media/external
```
Replace "/media/external" with whatever mount point you created for the filesystem. The UUID should reference a partition formatted with a filesystem like ext4. Run "sudo blkid" to make sure you have the correct UUID. For the filesystem above, blkid returns
```
/dev/sdf1: UUID="62bc0cab-e5e7-4bb3-9500-79e7e666ee27" TYPE="ext4" 
```

---

### Post by larryb1607 on 2020-09-05
Used the last suggestion by SeijiSensei.  Not sure if I created a mount point or not.  I was able copy the files I wanted to the USB folder I created by copying them from another place and opening the destination folder as admin.

---

