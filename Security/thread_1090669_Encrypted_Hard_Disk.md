---
title: "Encrypted Hard Disk"
date: 2009-03-08
forum: Security
---

### Post by AnotherDave on 2009-03-08
I have the standard encrypted installation of Intrepid. Does that mean that any hard disks added at my Home mount point will be encrypted as well?

Maybe this would be a good time to also ask how this disk encryption can be verified.

---

### Post by Tubes6al4v on 2009-03-08
Well, if you used the alternate CD and selected guided encryption, you are set. But if you tried to configure it yourself, or you just made an encrypted home (isn't that available in the Live CD? I never use that), then I don't know.

---

### Post by AnotherDave on 2009-03-08
I guess I'm set! But it would be nice to be able to verify this, somehow.

---

### Post by Tubes6al4v on 2009-03-09
Well, you could load another OS or liveCD and try to mount the drive. If it is encrypted you will need to use FreeOTFE (windows) or dm-crypt (linux) to open it.

---

### Post by hyper_ch on 2009-03-09
by default it encrypts everything durning installation. If you then decide to replace a mount point with a different partition/harddisk then that is NOT encrypted by default.

Also have multiple partitions means that you need to unlock them individually. You can use keys stored on the root partition to unlock subsequential partitions automatically if you want.

As to your question: they will not be encrypted.

---

### Post by AnotherDave on 2009-03-09
I'm starting to understand some of this now, thanks for the help. There is very little that I can find about adding a second hard disk, and nothing at all about how to make it work with the "alternate CD and selected guided encryption" on the first HD.

I repartitioned my second hard drive using fdisk and mkfs.ext3 on a spare machine. It shows up as a symbol on my desktop, and also as media in Places. I can mount and unmount by clicking on it, but cannot open a folder or paste any data to it.

---

### Post by hyper_ch on 2009-03-09
what do you try to do?

---

### Post by AnotherDave on 2009-03-09
hyper_ch: I'm running out of disk space, and trying to add a second hard drive. Encrypted, if possible.

I presently have an encrypted hard disk, via the "alternate CD and selected guided encryption" install, as Tubes6al4v describes it. 

I partitioned and formatted a second hard drive, using cfdisk and mkfs.ext3 on a different machine, then plugged it into my Ubuntu system.

It shows as a symbol on the desktop. I click on the symbol and a dialog comes up. I give my user password (not the disk encryption password) and the HD then mounts. I see a lost+found folder, but cannot create new folders, or move any data to this drive. 

Thanks for the help!

---

### Post by hyper_ch on 2009-03-09
you need to encrypt it first and then you can format it.

Check in my two guides the following steps

(1) for encryption the harddisk (or partition):

[http://www.howtoforge.com/ubuntu_dm_crypt_luks](http://www.howtoforge.com/ubuntu_dm_crypt_luks)  --> beginning from step V

(2) how you can auto-unlock the newly added partition during boot:

[http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

---

### Post by AnotherDave on 2009-03-09
hyper_ch: I'm with you, up to the mount at VIII. 
> sudo mount /dev/mapper/sdb /media/sleepy 
Returns
mount: special device /dev/mapper/sdb does not exist

I do see my DEVICENAME /dev/mapper/sleepy from step VII. Maybe I transposed something? 

Also, am I correct in using "sdb" for the HARDDISK? I don't see a partition number for my added drive when I fdisk -l.

---

### Post by hyper_ch on 2009-03-10
well, you have to use the mapper name ;) in your example you don't... you use "sdb" and not your "/dev/mapper/sleepy"

---

### Post by AnotherDave on 2009-03-10
> **VIII. Mount the partition**

...

Then mount the partition to the mounting point:

sudo mount /dev/mapper/HARDDISK /media/DEVICENAME

I'm using 'sdb' as HARDDISK, and 'sleepy' as DEVICENAME throughout **V - VII**. So, 

> sudo mount /dev/mapper/sdb /media/sleepy
Right?

If not, where do the names change? What is the "mapper name" you refer to in the last post?

---

### Post by hyper_ch on 2009-03-10
you don't use the harddisk but the mapped name

[http://en.wikipedia.org/wiki/Device_mapper](http://en.wikipedia.org/wiki/Device_mapper)

---

### Post by AnotherDave on 2009-03-10
Thank you for your patience! I must be missing something very simple. 

Maybe an example would be useful, using my actual input:

**V. Create the crypto partition**

sudo cryptsetup luksFormat /dev/HARDDISK

*~$ sudo cryptsetup luksFormat /dev/sdb*

(Asks for sudo pw, gives overwrite warning, gets passphrase, verifies passphrase. Command sucessful.)

**VI. Mapping the crypto partition**

sudo cryptsetup luksOpen /dev/HARDDISK DEVICENAME

*~$ sudo cryptsetup luksOpen /dev/sdb sleepy*

(Gets passphrase, unlocks slot. Command successful.)

**VII. Format the crypto partition**

sudo mkfs.ext3 /dev/mapper/DEVICENAME

*~$ sudo mkfs.ext3 /dev/mapper/sleepy*

mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
45793280 inodes, 183143517 blocks
9157175 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
5590 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 31 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

**VIII. Mount the partition**

sudo mkdir /media/DEVICENAME

*~$ sudo mkdir /media/sleepy*

(Returns prompt.)

sudo mount /dev/mapper/HARDDISK /media/DEVICENAME

*~$ sudo mount /dev/mapper/sdb /media/sleepy*

(Returns
mount: special device /dev/mapper/sdb does not exist)

---

### Post by hyper_ch on 2009-03-10
(1) you should not use a harddisk like that but first make a partition on it (even if it fills the whole harddiks)

(2) my mistake:


sudo mount /dev/mapper/HARDDISK /media/DEVICENAME

should be


sudo mount /dev/mapper/DEVICENAME /media/DEVICENAME

---

### Post by AnotherDave on 2009-03-10
> (1) you should not use a harddisk like that but first make a partition on it (even if it fills the whole harddiks)

I wondered about that in my #10 post.

> (2) ...

Ah ha! ;-) Now I understand.

Thanks for the help! :D

---

### Post by AnotherDave on 2009-03-26
Following your instructions thru 'VIII. Mount the partition' I now have a 750.2 GB Media 'sleepy' directory under Places in my file browser, containing a lost+found directory. But this folder cannot be opened, and no new folders can be created, and no folders or files can be dragged to it.

Maybe I should continue with tutorial to 'IX. Mount at bootup'?? 

But first action is to modify /etc/crypttab with 

> /dev/HARDDISK	none	luks,check=ext2,retry=5

Is this correct? New HD has ext3 file system, per step VII.

I'd prefer to leave this disk unmounted at boot, and use it only occasionally, so maybe mount at bootup is unnecessary?

---

### Post by hyper_ch on 2009-03-27
no, crypttab looks differently. See step 9 at my guide:

crypttab:
```

DEVICENAME	/dev/HARDDISK	none	luks,check=ext2,retry=5

```

fstab:
```

/dev/mapper/DEVICENAME	/media/HARDDISK	auto	defaults	0	0

```

---

### Post by AnotherDave on 2009-03-27
Doesn't work. The system only asks for the password of the original system drive at bootup (new drive has a different password). And it does not show the new drive after boot.

Again, I would prefer to mount the new encrypted drive only occasionally, after boot. Apparently something more than *sudo mount /dev/mapper/sleepy /media/sleepy* needs to be done.

---

### Post by hyper_ch on 2009-03-28
well, you'll probably need to recreate your initrd but I'd use a key to automatic unlock it anyway.

---

### Post by AnotherDave on 2009-03-28
> well, you'll probably need to recreate your initrd but I'd use a key to automatic unlock it anyway.

What does this mean?

All that I want to do is to mount and unmount the new, encrypted HD.

---

### Post by hyper_ch on 2009-03-28
see the links I've proveded at the beginning.

---

### Post by AnotherDave on 2009-03-29
> see the links I've proveded at the beginning. 

I think it might be good to review at this point:

 1) Completed [http://www.howtoforge.com/ubuntu_dm_crypt_luks](http://www.howtoforge.com/ubuntu_dm_crypt_luks) step 5 thru step 9, with revision to step 8, as per above.

 2) System boots normally, asking for password of existing HD, then floods screen with "xxxxxx" before resuming normal boot.

 3) System does not ask for password of the added HD.

 4) Ubuntu does not show added HD.

---

### Post by hyper_ch on 2009-03-29
you think you have to redo the initrd... but that shouldn't be necessary... hmmm

---

### Post by AnotherDave on 2009-03-29
No. I don't know a thing about initrd. You brought it up in #20 of this thread. 

I'm having trouble following your instructions. Could you please look again at my #23 and show me where I am going wrong.

---

### Post by AnotherDave on 2009-03-30
I think I see a pattern developing here.

This thread has been just silly. Anyone with Intrepid might be better served to use other sources for disk encryption advice.

---

### Post by hyper_ch on 2009-03-31
I know that my howtos work :)

---

### Post by AnotherDave on 2009-03-31
> I know that my howtos work 
And I know that YOU know your howto DIDN'T work. And that you had to correct it (see #15 of this thread).

When I asked about ANOTHER coding error in the same tutorial, you began acting weird and unhelpful.

And the error is still there.

I'd like to warn others adding a second encrypted disk that they may have trouble following your examples.

---

### Post by hyper_ch on 2009-03-31
> **AnotherDave said:**
> And I know that YOU know your howto DIDN'T work. And that you had to correct it (see #15 of this thread).
Well, just misnaming two things. If you did use your brain you would have spotted it yourself. However it still works ;)

> **AnotherDave said:**
> When I asked about ANOTHER coding error in the same tutorial, you began acting weird and unhelpful.
Where? When? It was rather you who started to act weird. Besides, you keep forgetting that you are not entitled to receive help. You keep forgetting everything here is on a voluntary base.

> **AnotherDave said:**
> And the error is still there.
Then you do something wrong.

> **AnotherDave said:**
> I'd like to warn others adding a second encrypted disk that they may have trouble following your examples.
Yet it works.

---

