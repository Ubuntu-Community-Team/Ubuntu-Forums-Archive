---
title: "How can I access other HDD with my server setup?"
date: 2015-10-17
forum: Server Platforms
---

### Post by concretecork on 2015-10-17
I have a newly built computer with 5 hot swap bays.
one of my drives has a windows OS on it.
three other ones are filled with data that I would like to access through my server.
[http://www.instructables.com/id/How-to-Host-Your-Own-Cloud-v20/](http://www.instructables.com/id/How-to-Host-Your-Own-Cloud-v20/)
I followed this tutorial but cannot figure out how to add access to these disks without transferring my data to the HDD that the server is installed on.
There is to much data on these HDD's to fit on the server drive.

---

### Post by TheFu on 2015-10-17
Are all of  these drives physically attached to the server?
Do they each have Linux readable file systems?
Has the fstab been modified to mount the disks?  I wouldn't do this for temporary storage, just permanent storage.

fstab how-to: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by concretecork on 2015-10-17
> **TheFu said:**
> Are all of  these drives physically attached to the server?
Yes, but I do pull them out from time to time when I'm connecting to the internet to keep them inaccessible from intruders

> **TheFu said:**
> Do they each have Linux readable file systems?
NTFS

> **TheFu said:**
> Has the fstab been modified to mount the disks?
No

> **TheFu said:**
> I wouldn't do this for temporary storage, just permanent storage.
Like I said I disconnect at times but drive letter shouldn't change when reinserted.

> **TheFu said:**
>  I wouldn't do this for temporary storage, just permanent storage.

fstab how-to: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) So Is this the way to go?
And thank you for your response

EDIT: So if I was going to go the fstab route I would edit fstab config file by adding...
For HDD drive E: 
E: "Mount point here, but not sure what it would be" NTFS-3g "not sure what to enter for options" 0 2
Sorry this is all new to me

---

### Post by TheFu on 2015-10-17
Drive letter? What's that?  That is **not** how Unix works.

Some things to keep in mind as you do more reading ... these are to make your life easier and not because you cannot do what you want, just it will make your life hard for very little payback.

* do not use spaces in directories or "mount_points"
* do not use special characters in directories or mount_points
* do not mount anything under /media/ or /mnt/ or under your HOME.
* create a locate for mounting. I use /D or /Data for media.
* do NOT pull a drive that is mounted. You must unmount it first which  will clear  any disk buffers and can take a few minutes to complete. The actual command is **umount** - without the 'n'.

There are reasons for these things. Other people may disagree.
If you must use NTFS,  then please understand that file and directory permissions are only controlled with mount options. You can learn about mount option in the manpages for both **mount** and **mount.ntfs**. I don't use NTFS storage, so can't just copy/paste my settings here. Sorry.  There are lots of NTFS mount questions in these forums and example fstab entries. Be certain that you understand each field in the fstab line.  

BTW, use **sudoedit /etc/fstab** for a safe way to edit system files. The EDITOR environment variable controls which editor will be used. I think it defaults to nano, but don't quote me. 

I do not use the fstab for USB connected storage, but most people do.

---

