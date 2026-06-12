---
title: "fsck completes extremely quick on ext3"
date: 2009-11-19
forum: Server Platforms
---

### Post by osx on 2009-11-19
I have a 32 GB partition, running Ubuntu 9.04, formatted with ext3. I decided to boot the system with an Ubuntu 9.10 cd in order to run fsck on the 32 GB partition. The command I ran was:
```

fsck -t ext3 /dev/sda3
```

Everything seemed fine, but it completed in about 1 second. Is this normal? Can fsck really check an ext3 partition that fast? Am I just used to a Windows filesystem check taking longer?

Thanks.

---

### Post by spikyjt on 2009-11-20
Yes if there are no errors. Ext3 is a journaling file system, so it only needs to read the journal to check for errors, which takes very little time, even on a big disk.

The -t ext3 isn't necessary when just checking one disk, by the way.

---

### Post by ian dobson on 2009-11-20
Hi,

you can use the -f option to "force" a full check.

Regards
Ian Dobson

---

### Post by osx on 2009-11-20
> **ian dobson said:**
> Hi,

you can use the -f option to "force" a full check.

Regards
Ian Dobson

Ian,

I don't see the "-f" option in the fsck man page. Nor do I see anything else in the man page regarding the ability to force a full check.

Are you sure that is an option? If so, what then is running fsck without "-f" doing to check the system? I haven't manually run the command before, but when I see it happen on boot it does take longer and appear to be doing more.

Thanks.

---

### Post by osx on 2009-11-20
> **spikyjt said:**
> Yes if there are no errors. Ext3 is a journaling file system, so it only needs to read the journal to check for errors, which takes very little time, even on a big disk.

The -t ext3 isn't necessary when just checking one disk, by the way.

spikyjt,

I should add that I am trying to learn fsck for a specific reason. I recently had a system running Ubuntu 8.04, 64-bit, server come up with errors on the screen which indicate a problem with the filesystem. I've not seen anything like it before, but it did indicated a problem with the filesystem. The computer is configured with two drives running in RAID 1.

When I tried to shutdown/reboot the system using standard commands, the system only repsonded with I/O error messages and would not respond to the commands normally. I pulled the power from the computer, turned it back on, and watched the screen for fsck to run. However, all fsck reported was the same as what I mentioned in my original post. In my original post, I manually ran the fsck command on the 32 GB partition to test how it worked. When it produced the same results as what I saw on the server, it concerned me that fsck may not be catching errors that it should.

I took the two drives out and ran the manufacturer's diagnostic software on them. Both passed so it could be a problem with the RAID controller; however, given the numerous error messages I saw that indicated a problem with the filesystem, it just seems like fsck should be doing a more thorough check.

Here's an example of the errors:

[13112496.301748] EXT3-fs error (device dm-0): ext3_find_entry: reading directory #475182 offset 0

Am I wrong in assuming there are filesystem errors?

Thanks.

---

### Post by ian dobson on 2009-11-21
Hi,

Reboot the box and in the grub menu select the recovery console.

Then go to the terminal prompt and do a 

e2fsck -f <device name>

Here's the helptext from e2fsck

```
root@alpha2:~# e2fsck --help
e2fsck: invalid option -- '-'
Usage: e2fsck [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
                [-I inode_buffer_blocks] [-P process_inode_size]
                [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
                [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
**_ -f                   Force checking even if filesystem is marked clean_**
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
```


The error you're seeing looks like abit of file system corruption, not a major problem but it's better to fix it before it get worse.

Regards
Ian Dobson

---

### Post by osx on 2009-11-21
Thanks, Ian. That explains why "-f" isn't in the fsck man page.

Can you give me an idea as to why fsck didn't do this automatically on reboot and only checked the journal instead?

---

### Post by ian dobson on 2009-11-21
Hi,

An fsck will run on boot if the file system as been mounted X times or X days since the last check or if the the filesystem wasn't shutdown cleanly. In your case you may have hit a bug in the ext3 code, a disk error, a memory error or some application error that caused a bad directory entry to be written to the disk.

I don't think you've go a major problem, just boot in single user mode and run a fsck on your drives.

Regards
Ian Dobson

---

