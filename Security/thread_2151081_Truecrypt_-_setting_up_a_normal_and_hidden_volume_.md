---
title: "Truecrypt - setting up a normal and hidden volume from the console"
date: 2013-06-03
forum: Security
---

### Post by Telside on 2013-06-03
Welcome.

Is this the correct procedure for the creation of a normal (outer) volume and the hidden volume?

1 truecrypt --volume-type = normal -c /dev/md0
2 assumption of the file system from the TrueCrypt
3 truecrypt --volume-type = hidden -c /dev/md0
4 assumption of the file system from the TrueCrypt

I found a few examples that the file system is assumed from the system (mkfs.ext4). TrueCrypt says something like this:

[I]Inexperienced users Should use the graphical user interface to create a hidden
volume. When using the text user interface, The Following procedure must be
Followed to create a hidden volume:
**1) Create an outer volume with no filesystem.**
2) Create a hidden volume within the outer volume.
3) Mount the outer volume using hidden volume protection.
4) Create a file system on the virtual device of the outer volume.
5) Mount the new file system and fill it with data.
6) Dismount the outer volume.
If at any step of the hidden volume protection is triggered, start again from 1).[/I]

Is there the difference between the two procedures (from the point of view of operation on the encrypted partition)? Because at first glance, everything seems to be working around (i used first procedure)?

I made a mistake in a given volume size hidden. Normal volume is low on space and you can not upload anything on it, and the system reports errors when mounting. Hidden volume is simply too large. How can I reduce the size of the hidden volume without re-encryption (setting) a normal volume? Is it enough to simply re-create a hidden volume with lower value?

Thank you for your help.

*I apologize for any errors. The text was translated by Google Translate.*

---

