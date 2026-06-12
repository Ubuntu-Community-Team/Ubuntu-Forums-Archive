---
title: "Cannot Edit a File / With Appropriate Permissions"
date: 2008-03-24
forum: Security Discussions
---

### Post by metradynamix on 2008-03-24
I had to give access to my server to someone temporarily. 
To get my networking functioning again. Datacenter

For some reason, I cannot edit my /etc/network/interfaces

A ls -la on /etc/network/interfaces returns: 
-rw-r--r-- 1 root root 133 2008-03-24 17:23 /etc/network/interfaces

Even when I su -s and try to make changes in the file I can't. 
I tried to delete the file and re-create and can't do that.

I keep on getting Operation not permitted.

Can someone please assist me in uncovering what was done, and how I can unlock this file.

Thank you.

---

### Post by codeslicer on 2008-03-24
Perhaps some other program has locked it. Did you try pressing Alt+2 and running "gksu gedit /etc/network/interfaces"? And doesn't the graphical tool work? If all else fails, boot into a live cd, mount the partition, and edit it from there.

---

### Post by metradynamix on 2008-03-24
That is the catch 22, I can't boot from a Live CD. I only have SSH Access and FreeNX access to this. This server is about 300 miles away from me.

> **codeslicer said:**
> Perhaps some other program has locked it. Did you try pressing Alt+2 and running "gksu gedit /etc/network/interfaces"? And doesn't the graphical tool work? If all else fails, boot into a live cd, mount the partition, and edit it from there.

---

### Post by metradynamix on 2008-03-24
What I gathered was that his statement was:

I have mod the file so no one else can modify it.

Is there a command that will lock a file? I looked at the permissions on the directory /etc/network and they seem normal as well. I can read the file, but can't edit it. 

> **metradynamix said:**
> That is the catch 22, I can't boot from a Live CD. I only have SSH Access and FreeNX access to this. This server is about 300 miles away from me.

---

### Post by codeslicer on 2008-03-24
Hmm... that's really strange. Sudo nano /etc/network/interfaces doesn't work either? I think that while the internet connection is active you can't edit /etc/network/interfaces - it is in use by whatever is connecting the two computers together. Perhaps you could somehow make a boot script which will change the file at boot, before you connect?

---

### Post by metradynamix on 2008-03-24
> **codeslicer said:**
> Hmm... that's really strange. Sudo nano /etc/network/interfaces doesn't work either? I think that while the internet connection is active you can't edit /etc/network/interfaces - it is in use by whatever is connecting the two computers together. Perhaps you could somehow make a boot script which will change the file at boot, before you connect?

sudo nano /etc/network/interfaces

Does open the file and I am capable of viewing it. I am unable to save any changes to the file.

---

### Post by The Cog on 2008-03-25
Just a thought. Try 
```
lsattr /etc/network/interfaces
lsof | grep /etc/network/interfaces
```
To see if any special attributes hae been set, or some process is holding it open.

---

