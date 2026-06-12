---
title: "Random tech question"
date: 2009-01-24
forum: The Cafe
---

### Post by butlins on 2009-01-24
When a computer comes from a
factory the harddisk is filled
with zeros and then the operating
system is loaded in.
The area that i ask about is the
part of the disk where nothing is stored.
If all the programs/kernel are placed at
the begining of the disk then most of it
must be empty or is the whole disk covered
from start to end with the file system,
obviously the file system would be written
over the zeros but what does it look like
through an Hex editor?

This post could be in the wrong area. if 
it's moved could the mod pm me with its
location as i have little time to search
this huge forum atm ;)

---

### Post by mips on 2009-01-24
Image part of it with dd and look at the output in an editor of your choice.

---

### Post by -grubby on 2009-01-24
Your post reads like a poorly written poem (all the \ns [line breaks] don't help)

---

### Post by Dr Small on 2009-01-24
> **nathangrubb said:**
> Your post reads like a poorly written poem (all the \ns [line breaks] don't help)
lol. I started to read it like a poem too! :p

---

### Post by butlins on 2009-01-24
> **nathangrubb said:**
> Your post reads like a poorly written poem (all the \ns [line breaks] don't help)

You have'nt heard my singing yet

---

### Post by schauerlich on 2009-01-24
A platter is formed
hard and disk like
the bits of potentiality wash across its smooth surface
dancing
like middle aged drunk men at weddings
what knowledge does this platter contain?
the ingredients of that sacred drink
the elixir of life, sought for milenia?
like those before me I set to discover
the secrets within
with a red bull
and funyons
I hacked away late into the night
after many an hour
and many a line of code
the secret was mine
$ cat /.secret.txt
42
$

---

### Post by RichardLinx on 2009-01-24
This thread is just funny. :D

---

### Post by Frak on 2009-01-24
> **RichardLinx said:**
> This thread is just funny. :D
O
rly?

---

### Post by Kingsley on 2009-01-24
> **nathangrubb said:**
> Your post reads like a poorly written poem (all the \ns [line breaks] don't help)
Yeah, you don't need to manually make margins.

---

### Post by az on 2009-01-24
I think the original poster is asking what an ext3 filesystem looks like on disk.  For example, is it striped or is all the fileystem data at the beginning of the drive.

I don't really know.  You can see for yourself, however.  Create a filesystem on a loop device (regular file) and then look at it in a hex editor:

andy@andy-desktop:~$ mkdir ext
andy@andy-desktop:~$ cd ext
andy@andy-desktop:~/ext$ dd if=/dev/zero of=file bs=1 count=1 seek=1M
1+0 records in
1+0 records out
1 byte (1 B) copied, 0.000149408 seconds, 6.7 kB/s
andy@andy-desktop:~/ext$ mkfs.ext3 file
mke2fs 1.40.2 (12-Jul-2007)
file is not a block special device.
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
128 inodes, 1024 blocks
51 blocks (4.98%) reserved for the super user
First data block=1
Maximum filesystem blocks=1048576
1 block group
8192 blocks per group, 8192 fragments per group
128 inodes per group

Writing inode tables: done                            

Filesystem too small for a journal
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 34 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

The file named "file" now contains an ext filesystem.  It is a sparse file, so it apears to be bigger than it actually is; the zeros don't take up any disk space.  In this example the majority of the file contains zeros and they are all at then end of the file.  But it's small and doesn't have a journal.  Perhaps a bigger file would appear differently.

I have tarred and gziped it and have attached it here:

---

