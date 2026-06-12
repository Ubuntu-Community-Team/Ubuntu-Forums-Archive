---
title: "error : attempt to read or write outside of disk 'hd0'"
date: 2015-11-26
forum: Server Platforms
---

### Post by soamz on 2015-11-26
I just wiped my server by doing reset config in RAID control and setup both disks to one RAID0. 
And then installed Ubuntu server. 

And now when it has booted, it shows this, 

> error : attempt to read or write outside of disk 'hd0'
Entering rescue mode
grub rescue >


WHAT TO DO ???

---

### Post by darkod on 2015-11-26
I am not sure it can work with raid0 because raid0 is splitting the files in half (the data). Usually linux boot files can not handled being split.

Why are you using raid0 anyway? If one disk dies, you lose all the data. You don't do that on a server, unless you don't care at all about the data on it.

Also check the partitions layout on the raid disk (array). One of the partitions really could be going "out" of the array.

You should be able to check partitions from live mode (using the desktop CD) with:
[code]sudo parted -l{/code]

---

### Post by soamz on 2015-11-26
> **darkod said:**
> I am not sure it can work with raid0 because raid0 is splitting the files in half (the data). Usually linux boot files can not handled being split.

Why are you using raid0 anyway? If one disk dies, you lose all the data. You don't do that on a server, unless you don't care at all about the data on it.

Also check the partitions layout on the raid disk (array). One of the partitions really could be going "out" of the array.

You should be able to check partitions from live mode (using the desktop CD) with:
[code]sudo parted -l{/code]


So use what ?
RAID5 ?

---

### Post by darkod on 2015-11-26
It depends on you. It also depends on number of disks. For raid5 you need minimum of 3 disks. If you have 5 disks for example, you can even make one raid1 array of 2 disks (mirror), and one raid5 of 3 disks. That way you can have the main OS and the data on different arrays.

There are many possibilities and it all depends on your planning for the server.

You can also use linux software raid (mdadm) instead of the server raid card. Some people prefer this because it's more flexible and often easy to recover from a failure. With mdadm raid you can move the disks on another completely different machine and still recover the data. With the built-in raid card, it will create the arrays in its own way and most often you can't move them to another machine or another raid card. For example, what if the raid card dies on you? You might lose all the data just because that one component failed.

But some servers with raid cards sometimes don't allow you to use the disks unless you use them in raid. They do not simply present them directly to the OS. That's the bad thing about branded servers and their raid cards. For mdadm you need the disks simply to be passed on as ordinary disks, because the ubuntu OS will create the raid.

---

