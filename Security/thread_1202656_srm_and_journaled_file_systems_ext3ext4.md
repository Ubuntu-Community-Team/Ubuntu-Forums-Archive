---
title: "srm and journaled file systems ext3/ext4"
date: 2009-07-02
forum: Security
---

### Post by shaggy999 on 2009-07-02
My understanding is that wiping a file on a journaled file system doesn't work because it doesn't wipe the data in the journal. What I am wondering is what is actually contained in the journal and is there a way to wipe the journal itself and then create a new one?

I am also curious about the effectives of wiping files in ext3 vs ext4. I currently use srm to wipe files. My understanding is that if you mount an ext3 in ordered data mode, which is the default, then the entire file (ignoring the journal) is effectively wiped. But my understanding is that ext4 by default is not in ordered mode? Is this correct? Is srm still effective on ext4 (excluding the journaled data)? Is it as simple as simply re-mounting in ordered mode or does the data have to be originally written in ordered mode?

---

### Post by lemming465 on 2009-07-04
> what is actually contained in the journal
That depends on which filesystem it is (there are different designs), and the case of something like ext3 or ext4, which mount options were used.  In a log-structured filesystem such as nilfs there is only the journal.  With ext3/4, it depends.  In the default *data=ordered* mode for both of those, metadata is journaled but file data is written directly.  *data=journaled* is more like DB transactions, with everything written twice, first to the journal, and second to the inode (metadata) and file (plain data).  

The big differences between ext3 and ext4 aren't related to journaling, it's in stuff like the inode data element sizes, extents instead of indirect blocks, and the new block allocator.

> is there a way to wipe the journal itself and then create a new one
An ext3/4 journal is basically treated as a circular buffer, so if you write more junk in data=journal mode than the journal size it should have the side effect of erasing it.   You can also use *tune2fs* to remove an existing journal and then create a new one, at least on unmounted filesystems, but that would leave data on disk which was potentially subject to recovery with forensic tools until the blocks happened to be reused for something else.

> I am also curious about the effectiveness of wiping files in ext3 vs ext4.
There is no different that I am aware of.  A tool such as *srm* works by overwritting all of the data blocks in a file (and presumably doing an fsync()) before unlinking it.  This has the same effect in ext2, ext3, and ext4.  At that point forensic tools might still be able to get back some of the file metadata, but only fools with a lot of time and a scanning electron microscope would be able to do probabalistic recovery of the actual data from any remnant magnetism.

The contents of a quiescent file with no dirty blocks in the buffer cache are fixed on disk; it doesn't matter what the journal mode was before the blocks were flushed.

Note that if you are really trying to keep data private, you need good control of the hardware and what runs on it.  In addition to the journal and file itself, you might have to worry about the swap space, so-called "cold boot" attacks against the memory, cache-timing side-channel attacks against process execution that leak cryptographic information, etc.  But the first step is to clear out the file data with a tool like *srm*, yes.

---

### Post by shaggy999 on 2009-07-04
Thanks for the helpful reply. It sounds to me like if someone wanted to (currently) ensure data was wiped without wiping the entire filesystem (assuming ext3/4) one could:

1) Wipe files with srm (this leaves metadata)
2) Dismount and remove the journal
3) Remount the filesystem in ext2 mode
4) Use sfill to wipe all free space (which should include the locations where the journal was stored)
5) Dismount and create a new journal
6) Remount as ext3/4

But it sounds like this is really only necessary in ordered=journal mode, which is NOT the default. Only metadata leaks out in the default mode.

We are, of course, ignoring hardware features like spare blocks on hdds and wear-leveling on flash devices and the other vectors of attack that you mentioned. I have read up on the cold boot attack you mentioned in relation to snatching encryption keys from memory. That makes me wonder, does dmcrypt overwrite the location of the encryption keys in memory when doing a full shutdown? That seems like a sensible deterrent.

In the future it sounds like there's some room for an 'sjournal' program that could be crafted to write data similiar to the srm/sfill/smem programs but to the journal space specifically, probably only when the filesystem is unmounted.

Computer security is so interesting. :)

---

### Post by lemming465 on 2009-07-04
You can't mount an ext4 filesystem as ext2 even if you do remove the journal; it has different on disk layout if it was ever mounted with option *extents*, which is kind of the main point of ext4.

I don't think you'll be able to use *sfill* on ext4 until it's been updated by someone to cope with the new disk layout.  In the absence of sfill, you'll get better journal wiping by writing junk files in data=journal mode than you will by removing the journal.  I'm not sure if ext4 will _let_ you remove the journal; I haven't tried that.

---

### Post by HermanAB on 2009-07-04
Encrypting a disk is easier than trying to erase files on an unencrypted file system.  Because of that simple fact, it is better to encrypt your /home and then you need not worry about deleting files.

Here is some info:
[http://aeronetworks.ca/luks-usb-howto.html](http://aeronetworks.ca/luks-usb-howto.html)

---

