---
title: "Nothing can save to usb drive through sftp"
date: 2016-07-13
forum: Server Platforms
---

### Post by max.schollen on 2016-07-13
hello 
I have a raspberry pi 3 with ubuntu mate
I like the Raspberry Pi running an SFTP server with an external drive (WD My Book 2TB)
The drive is formatted in fat 32
I can read through the server but I can not put anything on the disc!
Anyone have an idea what I can do about it preferably without data loss! 
Automatic mount is on!

---

### Post by TheFu on 2016-07-13
mount permissions. Fix those.

---

### Post by max.schollen on 2016-07-13
> **TheFu said:**
> mount permissions. Fix those.
Mount is on! (Automatic)

---

### Post by TheFu on 2016-07-13
> **max.schollen said:**
> Mount is on! (Automatic)

And you believe that does what you intend?  You can check them by ssh'ing in using the same userid. Try to touch a file on the same storage. Does it work or not? (I bet it doesn't).

I strongly suspect you'll need to configure something like autofs or udev to handle this to make it work the way you want.

Sorry, but I cannot test this - haven't allowed storage to be mounted by gvfs since ... er ... well, never. The power to mount is the power to destroy, IMHO.  gvfs works from a gnome GUI applications. Don't think it works at all without gnome (or some other DE) running.

Also, running 'mount' will show the mount options - check the permissions of the existing files on the storage. The owner and group are set by the mount options.

---

### Post by darkod on 2016-07-14
Let me add only this: "the drive formatted in FAT32"?????

First, do you need to share it with windows machines? If not, use a linux filesystem instead of fat32. And that will help a lot in better control of permissions in linux.

Second, fat32 is so old, and has many limitations. NTFS is used since ages ago. Even if you do need to share the disk with windows machines, use at least NTFS.

I agree with the above observation, the permissions decide who can write where. It's obvious your problem lies there. Check them out and assign as necessary...

---

### Post by max.schollen on 2016-07-14
> **darkod said:**
> Let me add only this: "the drive formatted in FAT32"?????

First, do you need to share it with windows machines? If not, use a linux filesystem instead of fat32. And that will help a lot in better control of permissions in linux.

Second, fat32 is so old, and has many limitations. NTFS is used since ages ago. Even if you do need to share the disk with windows machines, use at least NTFS.

I agree with the above observation, the permissions decide who can write where. It's obvious your problem lies there. Check them out and assign as necessary...
yes I thought so too
but I do not lose my files and nowhere else I save the files

---

### Post by TheFu on 2016-07-14
> **max.schollen said:**
> yes I thought so too
but I do not lose my files and nowhere else I save the files

Having a backup is a basic requirement for all files. Nothing can change that. How you elect to perform a backup is up to you. It isn't like lots of cash is needed with the $40 for 500G HDDs available.  Media files may not be deemed important enough to backup for everyone.  I wrestled with this myself for some time, then decided that $100 for a 4TB back disk WAS worth it to me. 

Still, the 1st issue remains. For NTFS and FAT32 disks, the easiest way to control which userid has write access it by controlling the mount options. Here's how I do it for USB devices ... actually have lots of different USB drives that this script mounts, if they exist. I use labels to control the mount locations - the partitions each have a unique label.
```
#!/bin/bash
UID=1000
GID=1000
LABEL1=PortMedia

# ensure the directory exists
sudo mkdir -p /mnt/$LABEL1

# mount it 
sudo mount -t vfat -o uid=$UID,gid=$GID LABEL=$LABEL1 /mnt/$LABEL1

```

For more mounts, just add LABEL2 at the tope and to the mkdir and add another mount command.

This is a very lazy way to do it - there are better ways and on other systems I use autofs for this stuff. For umounting, have a different script. Basically is does this ... 
```
sudo umount /mnt/$LABEL1
```

I suppose that pulling putting the LABELS into an array or into an external file would tied both scripts together nicely.  Or I could mount those that aren't already mounted and umount those that were.  Wouldn't be hard to merge both scripts.  I'm just lazy, like every great admin I know. ;)

Oh ... you'll need to make the UID and GID correct for your user, but 1000 : 1000 is normally the userid created at install time.
I mount outside the /media/ area on purpose.  To me, that is managed by automatic processes in the OS and I don't want any chance of interference with my manual mounts.  /mnt/ is for temporary mounts (by convention), which I follow. For permanent mounts, for data, I put those under /D/ or /Data/.  /D/ is nfs and /Data/ is CIFS.  That's my reasoning - use (or not) as you like. ;)

---

