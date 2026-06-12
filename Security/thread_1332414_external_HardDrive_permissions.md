---
title: "external HardDrive permissions"
date: 2009-11-20
forum: Security
---

### Post by evilbuntu on 2009-11-20
K I have been having trouble getting the ability to set up permission on my usb SimpleDrive NTFS 320 gb external hard drive. it used to work fine in all other earlier distributions but now it doesnt.

I use it to host my ftp and I am the owner and can get into it via Proftpd myself but non eo fmy users can.

I know its a permissions thing because "others" is set up to have none. I try to change it (under nautilus) but it just instantly changes back.

I tried to CHmod but its NTFS and that got me no where.

This is my FSTAB file

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/evilbuntu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=4b94d259-09a8-4278-a839-6c6d498ff11a /boot           ext2    defaults        0       2
/dev/mapper/evilbuntu-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


-------end------

I tried to add it into this many ways but it always tells me i dont have root priviledges to mount it after wards. This has been going on for a week now of constant searching and posting but nothing. I am in need of some help. Through googling i have seen i am not the only one with this issue but none of the remedies for anyone else has fixed it for me.

I have also tried plugging it into a windows machine multiple times (where it works fine) but it doesnt help on ubuntu 9.10.

thanks

---

### Post by cdenley on 2009-11-20
NTFS does not support linux permissions. The permissions are assigned at mount time. You must change the way the filesystem is mounted.
[http://ubuntuforums.org/showpost.php?p=4772289&postcount=4](http://ubuntuforums.org/showpost.php?p=4772289&postcount=4)

---

### Post by evilbuntu on 2009-11-20
i understand this issue but this hard drive has worked flawlessly the exact way it is since 8.04.

If i reformat the drive it will one, cause me to have to move all data off hten on. and will it be usable if i want to swap it to my windows machines.

the scripting in the post you gave me. should that be put into terminal or entered into my fstab?

thanks for being the ONLY reply all week

---

### Post by cdenley on 2009-11-20
This is a command, and should be run from the terminal.
```

gconftool -s /system/storage/default_options/ntfs-3g/mount_options \
 -t list --list-type string \
[locale=,exec,umask=000]

```
That would change your user's settings so any NTFS filesystems you mount with nautilus will have full rwx permissions. You could also create a new entry in /etc/fstab. You do not have to reformat. If you were able to change permissions on NTFS previously, it was not persistent. The filesystem cannot store unix permissions.

---

### Post by evilbuntu on 2009-11-20
tried it in terminal, it didnt work......

i picked a bad time to update linux and to windows 7 lol

edit again - just redid it a differant way and got "must specify a type when setting a value"; any ideas?

thanks again

edit:

actually should i run that command and then reboot? also when i run the command i get no comfirmation of any sort it just drops to a new terminal promtp

thanks again

---

### Post by cdenley on 2009-11-20
What do you mean didn't work? It shouldn't give you any output. It should change the mount options nautilus uses when mounting filesystems with the ntfs-3g driver. You can also do the same for ntfs for good measure.
```

gconftool -s /system/storage/default_options/ntfs/mount_options \
 -t list --list-type string \
[umask=000,utf8,exec]

```

---

### Post by lavinog on 2009-11-20
Here is a similar thread:[thread]1329975[/thread]
It is starting to look like there might be a bug regarding external hardrive permissions.

---

### Post by evilbuntu on 2009-11-20
> **cdenley said:**
> What do you mean didn't work? It shouldn't give you any output. It should change the mount options nautilus uses when mounting filesystems with the ntfs-3g driver. You can also do the same for ntfs for good measure.
```

gconftool -s /system/storage/default_options/ntfs/mount_options \
 -t list --list-type string \
[umask=000,utf8,exec]

```

maybe im not diong this right (thanks for dealing with my ignorance)

should i do it this way

myname: $ sudo gconftool -s /system/storage/default_options/ntfs/mount_options \ -t list --list-type string \

then be entering the [umask=000,utf8,exec] somehow? 

or just putting hte entire thing in at once the way it is.....?

thanks

---

### Post by cdenley on 2009-11-20
> **evilbuntu said:**
> maybe im not diong this right (thanks for dealing with my ignorance)

should i do it this way

myname: $ sudo gconftool -s /system/storage/default_options/ntfs/mount_options \ -t list --list-type string \

then be entering the [umask=000,utf8,exec] somehow? 

or just putting hte entire thing in at once the way it is.....?

thanks

No sudo! You're changing the setting for YOUR user, not root. (unless you mount the NTFS filesystem while running nautilus as root, which I don't recommend) If you put it all on one line, leave out the "\" characters.

```

gconftool -s /system/storage/default_options/ntfs/mount_options -t list --list-type string [umask=000,utf8,exec]

```

---

### Post by evilbuntu on 2009-11-20
well rebooting it now after running that code, keeping fingers crossed.

i just wanna get this set up so i can work on getting samba right with my win7 machine.

edit:

No luck........ sigh.

still cant get in with my user accounts and cant see nor make a visual differance in the drive permission properties.

---

### Post by ZhuaSD on 2009-11-26
I am having a similar problem with my (fat) drive, data transfer is choppy and hesitates.  Had it before and re-formatted, but I believe it is a mount problem.

You have to re-mount your drive to clear the problem.  When you first mount, an entry is made somewhere (like etc/mount), and then whenever you stick that drive in again it mounts through the same method.  That could be in your fstab but might not.

How is your drive mounted?

---

