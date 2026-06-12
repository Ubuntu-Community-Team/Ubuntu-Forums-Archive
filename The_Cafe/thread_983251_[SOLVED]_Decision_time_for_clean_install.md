---
title: "[SOLVED] Decision time for clean install"
date: 2008-11-15
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2008-11-15
I blew up the /sda3 trying to get gparted to grow it to absorb 64 gig of unallocated space. 

I'm going to do a clean install. But I want to keep the partions as they are:

sda1 is / of about 10 gig

sda3 is /home of about 280 gig

sda5 is swap of about 3 gig

I would like to pull all cookies, passwords, and stuff that isn't on /home but is part of my day-to-day use.

Also, I can only run Hardy in LiveCD to d/l the Intrepid .iso. I do have a 1 gig jumpdrive and could d/l it there, if it can be used to install the OS. Otherwise, can I d/l the .iso in LiveCD and then burn the .iso to a CD?

---

### Post by tom66 on 2008-11-15
Provided you have internet access and a flash/jump drive, then, yes you can download the LiveCD. You can even burn it to a CD, but it might be easier to actually format your flash/jump drive and put the contents of the live CD on that.

---

### Post by Mark_in_Hollywood on 2008-11-15
> **tom66 said:**
> Provided you have internet access and a flash/jump drive, then, yes you can download the LiveCD. You can even burn it to a CD, but it might be easier to actually format your flash/jump drive and put the contents of the live CD on that.

Can you point me to a resource that explains how to do the above, please?

---

### Post by Carl Hamlin on 2008-11-15
> **Mark_in_Hollywood said:**
> I blew up the /sda3 trying to get gparted to grow it to absorb 64 gig of unallocated space.

What happened there?

> **Mark_in_Hollywood said:**
> Also, I can only run Hardy in LiveCD to d/l the Intrepid .iso. I do have a 1 gig jumpdrive and could d/l it there, if it can be used to install the OS. Otherwise, can I d/l the .iso in LiveCD and then burn the .iso to a CD?

You *should* be able to burn the ISO image to CD-R from the Live CD, so long as you're not actually *booting* from the drive you want to write to.

---

### Post by Neostar on 2008-11-15
You can mount one of the partitions and use wget to download Ubuntu from an ftp server.

You can choose one that is near to you from this list.
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

> wget -c [http://ftp.ucsb.edu/pub/mirrors/linux/ubuntu/8.10/ubuntu-8.10-desktop-i386.iso](http://ftp.ucsb.edu/pub/mirrors/linux/ubuntu/8.10/ubuntu-8.10-desktop-i386.iso)

---

### Post by Mark_in_Hollywood on 2008-11-15
> **Neostar said:**
> You can mount one of the partitions and use wget to download Ubuntu from an ftp server.

You can choose one that is near to you from this list.
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

Mount one of WHICH partitions? Huh?

---

### Post by Neostar on 2008-11-15
Sorry you mount the /home partition and save your .iso file there.

Once it's complete you can then right-click and select burn iso.

---

### Post by Mark_in_Hollywood on 2008-11-16
Sorry, again, I dont' understand what you mean. I'm closing this thread and hoping for the best.

---

