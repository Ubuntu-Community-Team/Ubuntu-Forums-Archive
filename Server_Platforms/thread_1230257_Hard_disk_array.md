---
title: "Hard disk array"
date: 2009-08-03
forum: Server Platforms
---

### Post by ade234uk on 2009-08-03
I am moving everything off my hard drives to my own FTP server. I would be interested in learning how to set up a hard disk array, so I have two hard disks in case one fails. Hope I'm not going over the top with this.

I was thinking of buying a second hand server off ebay and then adding the drives, What do I need to look out for?

---

### Post by trundlenut on 2009-08-03
If you're going to buy a second hand server, get one with a hardware raid controller, so much easier to set up than software raid.  Though this will most likely be SCSI.  How much storage space will you need?

I would say raid 5 is probably better to go for than raid 1 (2 discs each with the same data in case of failure).  With raid 5 you need a minimum of 3 disks and it will cope with one disc failing and keep working.  The capacity of the array will be the capacity multiplied by the number of discs minus one. i.e. 3x36Gb discs gives 72Gb of space, 4x36=108 etc, you can also keep adding discs into the array but all the discs need to be the same size.

I have just setup a Dell Poweredge server with 2 36gb discs running raid1 and I'm going to get some more (3+) discs for data storage running raid5.

The big advantage of hardware raid is when I came to install ubuntu it saw the raid array as a single volume.  I just had to configure the array using the dell setup utility.

---

### Post by ade234uk on 2009-08-03
I think I will buy three scsi drives, looking for as big as possible over 3 drives, however these are bloody expensive. May be there is a server on ebay with them already in but I doubt it.

---

### Post by trundlenut on 2009-08-03
I got 2 36gb ultra 320 discs for about £28 for the pair from ebay.  I'm just using these to install ubuntu on.  I was thinking of gradually aquiring between 3 and 6 72gb drives as and when i see them for a good price.  On my dell server I believe you can add discs to an existing array.  These will be used for storage.  You maybe better off getting more smaller drives, but it will depend on how many you can put in it.

I was lucky and got the server for nothing but it had no drives in it.

---

