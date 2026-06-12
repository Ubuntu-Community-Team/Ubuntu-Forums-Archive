---
title: "Can't chown of Samba share"
date: 2010-07-26
forum: Server Platforms
---

### Post by z61P on 2010-07-26
I'm having some issues changing ownership on a Samba share, and I suspect it has something to do with how I mount the drive. Here's my setup:
 
The system has two physical hard drives in it, sda1 and sdb1. sda1 is the "primary" drive (the drive I installed the OS on). sdb1 is to be dedicated as a share for the Samba server. 
 
Here's my fstab entry for sdb1: 
 
/dev/sdb1 /samba/drive1 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=10 00,utf8,umask=077,flush 2 
 
Is this correct, or at least reasonable? I'm suspicious of the "vfat" option for some reason. 
 
And here's my smb.conf share declaration: 
 
[public]
path = /samba/drive1/public
valid users = @staff
writeable = Yes
read only = no
public = yes
available = yes
browsable = yes
 
My problem is that I can't actually see the contents of this share (e.g. the readme.txt file I created from the console) from a Windoze PC. I'm pretty sure that's because I don't have *nix* permissions set correctly. Here's what I mean: 
 
tpmoore@ubuntu1:/samba/drive1/public$ ls -la
total 48
drwx------ 2 tpmoore root 16384 2010-07-23 10:22 .
drwx------ 3 tpmoore root 16384 2010-07-23 09:33 ..
-rwx------ 1 tpmoore root 111 2010-07-23 10:22 readme.txt
 
Attempts to 'chown' of the share, or any files in it result in a polite refusal from the system, for example: 
 
tpmoore@ubuntu1:/samba/drive1/public$ sudo chown :staff readme.txt
[sudo] password for tpmoore:
chown: changing group of `readme.txt': Operation not permitted 
 
I could go on, but I'll stop now. I can provide additional details if needed. 
 
All clues appreciated. 
 
Best Rgds,
z

---

### Post by arrrghhh on 2010-07-26
Your suspicion is correct.  vfat = FAT32 (perhaps even FAT16 also) and permissions in Win-based systems is very different from permissions in *nix systems.

So either get that drive off of FAT32, or you can manipulate the permissions directly thru Samba (at least you should be able to...)

Also, did you try to chmod the files?  I don't think chown will work, but you should be able to chmod the files/folders...

---

### Post by Morbius1 on 2010-07-26
>  /dev/sdb1 /samba/drive1 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=10 00,utf8,umask=077,flush 2 Please tell me some GUI app created that line ;) I don't know if some of those are typos when you created your post or if the app did that but ....

Try something like this instead:
```
/dev/sdb1 /samba/drive1 vfat utf8,umask=000 0 2
```This will produce a mount point owned by root but with read / write access to everyone ( i.e., umask=000 ). Right now the only user that has access to the target folder is tpmoore. Samba determines who has the authorization to access but linux file permissions determines who has the ability to access.

I'm assuming from your original post that this is a partition on an internal hard drive and not a USB external drive. The fstab entry would be different if that were so.

---

### Post by z61P on 2010-07-26
> **arrrghhh said:**
> Your suspicion is correct. vfat = FAT32 (perhaps even FAT16 also) and permissions in Win-based systems is very different from permissions in *nix systems.
 
So either get that drive off of FAT32, or you can manipulate the permissions directly thru Samba (at least you should be able to...)
 
Also, did you try to chmod the files? I don't think chown will work, but you should be able to chmod the files/folders...
 
Thanks for the input... I reformatted the drive w/ the ext4 fs using mkfs (actually mke2fs), and now I'm "in control" again :) 
 
I didn't actually read your reply until after the reformat, but I think I tried chmod before posting for help, and it did not work either. 
 
Navigating the relationships between Samba permissions and Unix permissions is interesting, and this little trick with the fs type made it more so! I assumed I needed a vfat fs (WIndows clients, right?), but learned after some reading that Samba takes care of all necessary "fs translations" for you - sweet. 
 
I wonder though... is ext4 the "best" fs for Samba? 
 
z

---

### Post by arrrghhh on 2010-07-26
Glad it's workin for ya... Please use the "Thread Tools" drop-down to mark this thread [SOLVED].

As for your question about the "best" fs for samba... I don't think samba cares to be perfectly honest with you.  I would pick the best fs for what you're doing.... ext3/4 are very good for general use, although 4 has shown some odd bugs (it's still pretty new).  ZFS would probably be best if the file system is large... I'm not exactly an expert on file systems however, but those are my .02.

---

### Post by z61P on 2010-07-26
> **Morbius1 said:**
> Please tell me some GUI app created that line ;) I don't know if some of those are typos when you created your post or if the app did that but ....
 
Try something like this instead:
```
/dev/sdb1 /samba/drive1 vfat utf8,umask=000 0 2
```This will produce a mount point owned by root but with read / write access to everyone ( i.e., umask=000 ). Right now the only user that has access to the target folder is tpmoore. Samba determines who has the authorization to access but linux file permissions determines who has the ability to access.
 
I'm assuming from your original post that this is a partition on an internal hard drive and not a USB external drive. The fstab entry would be different if that were so.
 
I asked myself where I got that fstab line... I don't recall now. 
 
Do you think that your fstab entry would have allowed me to make chown changes? 
 
Yes - it's an internal HDD. I wanted all of the files from my Windoze users on a separate drive that I could move to a different machine if need be. I originally chose the vfat fs because I thought I could move the drive to a Windoze PC, and mount it there. However, due to my inability to chown the drive, I reformatted as ext4. 
 
So, I wonder: What's the best file system to use in this situation? 
 
Thanks,
z

---

### Post by Morbius1 on 2010-07-27
>  I didn't actually read your reply until after the reformat, but I think I  tried chmod before posting for help, and it did not work either. >  Do you think that your fstab entry would have allowed me to make chown changes? 2 different groups of filesystems - Windows ( NTFS & FAT32) and Linux ( ext3/4). You can't chown or chmod a windows filesystem, You can only change ownership and permissions on a Windows filesystem in a mount or in fstab.
>  So, I wonder: What's the best file system to use in this situation?  Technically, it doesn't matter. Samba uses a virtual filesystem called cifs which makes all source filesystems look the same to the client. 

But keep in mind the relationship between Samba authorizations and Linux file permissions. In your original mount of the FAT32 partition you set permissions to 700: Read and write to owner and no access to anyone else. Your samba share had " valid users = @staff" . The members of the @staff group are not the owners of the partition. Samba may "authorize" @staff to access the share but Linux will only "permit" the owner to access the folder. Samba can "take from" but not "add to" the permissions set by linux itself. You attempted to "add to" the linux file permissions.

In the new mount for the fat32 partition I set permissions so that anyone can access the partition ( umask=000). But by using "valid users = @staff" you limited remote authorization to only that group. This would have "taken from" the linux file permissions.

---

### Post by z61P on 2010-07-27
> **Morbius1 said:**
> 2 different groups of filesystems - Windows ( NTFS & FAT32) and Linux ( ext3/4). You can't chown or chmod a windows filesystem, You can only change ownership and permissions on a Windows filesystem in a mount or in fstab.
Technically, it doesn't matter. Samba uses a virtual filesystem called cifs which makes all source filesystems look the same to the client. 
 
But keep in mind the relationship between Samba authorizations and Linux file permissions. In your original mount of the FAT32 partition you set permissions to 700: Read and write to owner and no access to anyone else. Your samba share had " valid users = @staff" . The members of the @staff group are not the owners of the partition. Samba may "authorize" @staff to access the share but Linux will only "permit" the owner to access the folder. Samba can "take from" but not "add to" the permissions set by linux itself. You attempted to "add to" the linux file permissions.
 
In the new mount for the fat32 partition I set permissions so that anyone can access the partition ( umask=000). But by using "valid users = @staff" you limited remote authorization to only that group. This would have "taken from" the linux file permissions.
 
Thanks for that clarification. It appears that my big mistake was not in my choice of filesystem, but in the permissions I assigned when I mounted it. 
 
I think this thread is "SOLVED"; now I've just got to try to noodle through how to structure permissions. Look for more posts on that subject :) 
 
Best Rgds,
z

---

