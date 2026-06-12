---
title: "Origins of the Ext2/3/4 superblock magic number"
date: 2010-11-25
forum: The Cafe
---

### Post by Aikon- on 2010-11-25
As some of you may know, Ext2/3/4 have a magic number stored in the superblock of 0xEF53. I was wondering if anyone knows the origin of this number, and whether it was chosen for some specific reason, or selected at random?

The only pattern I have been able to discern is that the second byte, 0x53, is a palindrome.

-S

---

### Post by kidders on 2010-11-26
Hi there,

I don't really have an answer ... just a few thoughts that might spark something off in your head :-P[LIST]
[*]ASCII character code 0x53 is 'S' ... Do you suppose it's meant to be read as "EFS" (Extended File System)?
[*]Originally, Ext2's magic number was 0xEF51 ... Maybe *that's* the number that originally meant something to its developer. (It was changed to 0xEF53 after a tweak to the way filesystem group descriptors were stored caused a backward compatibility issue.)
[*]Ext2's superblock is mostly in little endian byte order, so the magic number actually reads ".. 53 EF .." on disk.
[/LIST]

To be honest, I'd put money on the answer being something boringly practical, like 
byte 1080 of the filesystem *had* to read "0101 XXXX" to avoid being mistaken for something else that was around at the time.

---

### Post by czr114 on 2010-11-26
0xEF51 is 61265 in dec.

Were any of the developers born June 12, 1965?

---

