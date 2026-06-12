---
title: "Trouble with Samba"
date: 2017-10-23
forum: Server Platforms
---

### Post by daenir on 2017-10-23
Hey all, new to Ubuntu Server 17.10.

I've been following this guide:
[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)

But the problem that occurs is that I can log in to my partitioned network drive but I can't interact with it.
I can't save files to it etc.

Here's my smb.comf

```
 

[Storage]
   comment = File Server
   path = /srv/samba/Storage
   browsable = yes
   guest ok = no
   read only = no
   create mask = 0755



```

Any help/guidelines would be much appreciated

---

### Post by wildmanne39 on 2017-10-23
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by Morbius1 on 2017-10-24
> **daenir said:**
> 

I've been following this guide:
[https://help.ubuntu.com/lts/serverguide/samba-fileserver.html](https://help.ubuntu.com/lts/serverguide/samba-fileserver.html)
[COLOR=#0000cd] Just so you know I use that linked document as an example of a bad Samba HowTO.[/COLOR]

If you followed those steps exactly as written your shared folder would have the following permissions:
> drwxr-xr-x 2 nobody nogroup
The only user that will gain write access to that share is "nobody" which will happen only if the client user is not required to pass credentials or in the case of a Windows client that user is never given a samba password.

The moment you changed "guest ok = yes" to "guest ok = no" it requires the client user to log into the server and at that point he is no longer "nobody".

One way out of this is to keep everything as it is now but add one more line to the share definition:
> [Storage]
   comment = File Server
   path = /srv/samba/Storage
   browsable = yes
   guest ok = no
   read only = no
   [COLOR=#0000cd]**force user = nobody**[/COLOR]
   create mask = 0755
Then restart samba:
```
sudo service smbd restart
```
The client user will still be required to pass credentials but when it's accepted it will be converted to the user "nobody" - at least for that share.

---

### Post by daenir on 2017-10-24
So after I tried just adding the one line of code it still did not work.

The following things I've tried:
* Removing and adding the directory again, making sure that it has those properties "nobody:nogroup"
* Adding valid users to smb.conf

Does the permissions mess up if /srv/Storage is mounted on another drive?

Is there any good HowTO's that you would recommend instead?

Edit: I also changed the file directory while adding new directory
```

[Storage]
   comment = File Server
   path = /srv/Storage
   browsable = yes
   guest ok = no
   read only = no
   force user = nobody
   valid users = emil, nobody
   create mask = 0755

```

---

### Post by Morbius1 on 2017-10-24
You are adding your users to the samba password database, right?

```
sudo smbpasswd -a emil
```

---

### Post by daenir on 2017-10-24
Yes, I did.

I think I've stumbled across the problem.
When following a guide it just used a directory on the main drive, but then later when I tried mounting a specific harddrive to it, it stopped working
So the drive where Ubuntu Server is located works fine, but not if I mount the directory to another drive

Any fix?

---

### Post by Morbius1 on 2017-10-24
>  So the drive where Ubuntu Server is located works fine, but not if I mount the directory to another drive
I don't even know what that means. Everything is mounted under "/" and that is where the OS is located.

Why not post the output of the following command so folks can see how this is set up:
```
cat /etc/fstab
```

---

### Post by daenir on 2017-10-24
Content of /etc/fstab

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/EMILSERVER--vg-root /               ext4    errors=remount-ro 0       1
/dev/mapper/EMILSERVER--vg-swap_1 none            swap    sw              0       0
/dev/sda /srv/samba/Storage vfat  defaults 0 0



```

The last line I wrote in myself while following a guide to format my drive

---

### Post by Morbius1 on 2017-10-24
Sorry, wasn't smart enough to ask for the next question - the output of this one:
```
sudo blkid -c /dev/null | grep vfat
```

---

### Post by daenir on 2017-10-24
> **Morbius1 said:**
> Sorry, wasn't smart enough to ask for the next question - the output of this one:
```
sudo blkid -c /dev/null | grep vfat
```
That command doesn't give me any output. I must be doing something wrong

---

### Post by Morbius1 on 2017-10-24
Try it again without the grep:
```
sudo blkid -c /dev/null
```
If it still has no output how about:
```
sudo parted -l /dev/sda
```

---

