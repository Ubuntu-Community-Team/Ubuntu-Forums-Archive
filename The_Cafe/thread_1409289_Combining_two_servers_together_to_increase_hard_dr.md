---
title: "Combining two servers together to increase hard drive space of system?"
date: 2010-02-17
forum: The Cafe
---

### Post by samh785 on 2010-02-17
I need to figure out how to combine two servers together for the purpose of increasing the total memory (hard drive space) of the system. I have absolutely no idea how I would go about doing this, and any tips/resources/help would be greatly appreciated. 

Sam

---

### Post by pirateghost on 2010-02-17
> **samh785 said:**
> I need to figure out how to combine two servers together for the purpose of increasing the total memory (hard drive space) of the system. I have absolutely no idea how I would go about doing this, and any tips/resources/help would be greatly appreciated. 

Sam
umm...why not just take the harddrive out of one and putting it in another??

for future reference memory refers to RAM, not harddrive space.  harddrive space would be considered storage.

---

### Post by samh785 on 2010-02-17
> **pirateghost said:**
> umm...why not just take the harddrive out of one and putting it in another??

for future reference memory refers to RAM, not harddrive space.  harddrive space would be considered storage.

The computers are extremely compact and as such, I cannot move the hard drive into one computer. Thank you for the tip about the terminology, I will refer to it as storage from now on.

---

### Post by pirateghost on 2010-02-17
> **samh785 said:**
> The computers are extremely compact and as such, I cannot move the hard drive into one computer. Thank you for the tip about the terminology, I will refer to it as storage from now on.
what you are asking for is extremely difficult and will be a huge learning curve.  have a look into GFS [http://en.wikipedia.org/wiki/Global_File_System](http://en.wikipedia.org/wiki/Global_File_System)

what you are wanting to do is create a cluster and utilize GFS for the storage.  this is a big task.  are you sure there are not other ways of achieving the desired end product?

---

### Post by samh785 on 2010-02-17
Well, if it's really that hard I suppose it would be best to attach an external hard drive or something.

---

### Post by tjwoosta on 2010-02-17
It doesnt have to be so complex.

You could just setup NFS on one of the machines and mount it with the other.

---

### Post by steveneddy on 2010-02-17
> **samh785 said:**
> Well, if it's really that hard I suppose it would be best to **attach an external hard drive** or something.

Perfect solution - external HD's are very convenient and easy to get running and transfer between other PC's.

---

### Post by Barrucadu on 2010-02-17
You could share their hard drives with SSHFS (or something similar), and then mount one on the other.

---

### Post by ssam on 2010-02-17
this might help
[http://en.wikipedia.org/wiki/Network_block_device](http://en.wikipedia.org/wiki/Network_block_device)
it can make a remote block device (like a disk) look like a local one, so that you could use raid across them.

or you could use a distributed filesystem. [http://en.wikipedia.org/wiki/List_of_file_systems#Distributed_file_systems](http://en.wikipedia.org/wiki/List_of_file_systems#Distributed_file_systems) eg POHMELFS. these may handle network problems better.

---

### Post by handy on 2010-02-17
I just use FreeNAS, it is simple, reliable & beautiful at the client side.

It may or may not be suitable for the OP?

---

### Post by The Real Dave on 2010-02-17
> **Barrucadu said:**
> You could share their hard drives with SSHFS (or something similar), and then mount one on the other.

Best off using NFS if you don't need the security of SSHFS. NFS is much faster, and less power consuming. It's been said already, GFS is difficult and finicky, your best off sharing the drive on one, and mounting it on the other. 

Say your sharing a folder on Server1, and mounting on Server2. Your best off to mount the folder to somewhere like /mnt/Server1 and make a symbolic link to that in the /home/user directory on Server2. That way, you get easy access, and you won't lock up your /home dir if Server1 is down. :)

If you mount the /home/user dir from Server2 onto another computer, as I presume you would be, a size check (using df -h) would show the size of /home/user on Server2 as being the size of /home/user on both Servers added together :)

Depending on your network hardware (100MBs or Gigabit), this will be faster than an external drive. Well, faster than a USB one at least.

---

### Post by samh785 on 2010-02-18
> **steveneddy said:**
> Perfect solution - external HD's are very convenient and easy to get running and transfer between other PC's.
:D yeah, I know I know... I just didn't want to go out and buy one.

---

### Post by thatguruguy on 2010-02-18
> **samh785 said:**
> :D yeah, I know I know... I just didn't want to go out and buy one.

You can always just get an [enclosure]("http://www.tigerdirect.com/applications/Category/category_tlc.asp?CatId=2777&name=Hard-Drive-Enclosure"), and use one of your existing drives.

---

