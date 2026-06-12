---
title: "Secure deletion of journaled files"
date: 2008-05-17
forum: Security
---

### Post by GeneralCody on 2008-05-17
There are many people out there that believe that tools like shred or wipe, will suffice for deleting files on their journaled file system, like ext3, ReiserFS etc.

They have obviously not read the manual page. 
Problem is that the man page just confirms that the tools are primarily meant to erase data "in-place", i.e. not on a system with journal entries, that can be used to recreate the files in question...

One way to achieve a deletion on a journaled file system is to dd the data with /dev/zero, use a sync() call, issue the wipe command, then issue another call to sync().

sync() is a POSIX call that writes buffered data to disk.
dd is a command that in this scenario will fill the upper layer (on the magnetic media) of the file with zeros, so that eventual metadata will disappear in the journal, after calling sync().

dd will keep on filling the file, extending its size, so this should be scripted, so that you can stop dd when filesize is over the size of the file you want to get rid of.
Ususally there will be a bunch of files in a directory, so some python or perl, would do the trick here.

An example would be in order:

```
notme@saywhat:~$ dd if=/dev/zero of=/home/notme/eraseme.txt
sync
notme@saywhat:~$ wipe /home/notme/eraseme.txt
sync
```wipe has many options, that you should care about. RTFM. 

I'm not 100% sure about this, but I believe this would be a good way to erase files on journaled file systems. 

Open for comments :-)

---

### Post by hyper_ch on 2008-05-17
I took the easy route and fully encrypted my system... so I don't worry about secure deleting any longer ;)

---

### Post by GeneralCody on 2008-05-18
> **hyper_ch said:**
> I took the easy route and fully encrypted my system... so I don't worry about secure deleting any longer ;)

quote wipe manpage:

*"Encrypting  a  whole  partition  with cryptoloop, for example, does not help very much either, since there is a single key for all  the  partition."*

so...

---

### Post by hyper_ch on 2008-05-18
so?

---

### Post by GeneralCody on 2008-05-18
So. Even if your fs is encrypted, files get decrypted on the fly, when in use, so deleting a file doesn't make the deletion secure. You could just as easy log in and recover the file.

---

### Post by hyper_ch on 2008-05-18
how? If everything is encrypted but /boot ?

---

### Post by GeneralCody on 2008-05-18
Depends. What do you use to encrypt your partitions?
Cryptoloop?

---

### Post by hyper_ch on 2008-05-18
dm_crypt/luks

---

### Post by GeneralCody on 2008-05-18
That's a good alternative for securing your data against being read by others, but encryption and deletion, actually doesn't have much to do with each other. 

No matter if the data is encrypted, the data can be recovered and decrypted by e.g. the government agencies. Secure deletion involves overwriting the magnetic media, to the extent that it can not be recovered. Usually about 30 layers down on the media.

Roger out.

---

### Post by hyper_ch on 2008-05-18
Encryption and secure deletion soe have much to do with each other... both aim at protecting the data...

and as there is no known security issue with dm_crypt (except for freezing your ram modules - but if you're worried about that, you have other problems)... so how would government agencies be able to access the encrypted data?

---

### Post by GeneralCody on 2008-05-18
By spending some time to find/crack the single encryption key that protects the partition.

NSA does this pretty often, but this is starting to remind me of paranoia ;-)

---

### Post by hyper_ch on 2008-05-18
and how many years do you want to give them for that?

---

### Post by GeneralCody on 2008-05-18
Depends on the cipher method and bit length, but a 512 bits RSA, would take about 7 months +/-. (according to NSA themselves)

So... Probably no need to worry, unless you're in custody.

---

### Post by jdong on 2008-05-19
> **GeneralCody said:**
> 
One way to achieve a deletion on a journaled file system is to dd the data with /dev/zero, use a sync() call, issue the wipe command, then issue another call to sync().

sync() is a POSIX call that writes buffered data to disk.
dd is a command that in this scenario will fill the upper layer (on the magnetic media) of the file with zeros, so that eventual metadata will disappear in the journal, after calling sync().

dd will keep on filling the file, extending its size, so this should be scripted, so that you can stop dd when filesize is over the size of the file you want to get rid of.
Ususally there will be a bunch of files in a directory, so some python or perl, would do the trick here.

An example would be in order:

```
notme@saywhat:~$ dd if=/dev/zero of=/home/notme/eraseme.txt
sync
notme@saywhat:~$ wipe /home/notme/eraseme.txt
sync
```wipe has many options, that you should care about. RTFM. 

I'm not 100% sure about this, but I believe this would be a good way to erase files on journaled file systems. 

Open for comments :-)

I'm personally not convinced by this... There's no guarantee that either one of these will hit the journal enough as to flood its default size (32MiB or so) and hence securely erase its contents. Also, journaled filesystems make LESS of a promise as to what "overwrite" or extend means, and since fsync-is-sync on ordered journaling filesystems this is effectively already done.

At this point I don't think it's safe to assume anything about secure deletion on journaled filesystems; if you need that level of security I'd still recommend full-disk encryption.


Phoronix did a benchmark with Ubuntu on FDE and found that on reasonably modern CPU's the process is disk-bound, not CPU bound.

---

### Post by jdong on 2008-05-19
> **hyper_ch said:**
> Encryption and secure deletion soe have much to do with each other... both aim at protecting the data...

and as there is no known security issue with dm_crypt (except for freezing your ram modules - but if you're worried about that, you have other problems)... so how would government agencies be able to access the encrypted data?

Oh that's a simple one.... in many jurisdictions, order you to turn over your key. Now you're between a rock and a hard spot.

---

### Post by hyper_ch on 2008-05-19
> **jdong said:**
> Oh that's a simple one.... in many jurisdictions, order you to turn over your key.
In many? I just know the US and England - although I think England is violating art. 6 ECHR in which it is acknowledged (unwritten) that you don't have to provide evidence against you.

---

### Post by GeneralCody on 2008-05-19
So the ultimate, must be ext2 on all partitions + strong encryption with salted keys...
Then you can use wipe on top, and be happy...

---

### Post by hyper_ch on 2008-05-19
or not store any files on the computer that need to be securly wiped ;)

---

### Post by GeneralCody on 2008-05-19
That is the safest option! Way to go!

:-)

---

### Post by /etc/init.d/ on 2008-05-19
> **GeneralCody said:**
> Depends on the cipher method and bit length, but a 512 bits RSA, would take about 7 months +/-. (according to NSA themselves)

So... Probably no need to worry, unless you're in custody.
RSA is not used for disk encryption.  Symmetric ciphers do the actual encryption, and many ciphers, such as AES, are considered to be secure given large enough key length and correct mode of operation.  And besides, 512 bits is a ridiculously small key length for RSA.  Knock that number up to 2048 bits, then see how long it'd take you.

---

### Post by GeneralCody on 2008-05-19
> **/etc/init.d/ said:**
> RSA is not used for disk encryption.  Symmetric ciphers do the actual encryption, and many ciphers, such as AES, are considered to be secure given large enough key length and correct mode of operation.  And besides, 512 bits is a ridiculously small key length for RSA.  Knock that number up to 2048 bits, then see how long it'd take you.

You really don't seem to understand cryptography but merely want to spread fear and your misguided paranoia.

Now that would be an overstatement. I'm no cryto expert, if you have the ability to read the whole thread, it wasn't even me that started to talk about encryption. My thread was about erasing files securely on a journaled file system, not about encryption, what so ever.

But thanks for the compliment. Everybody needs a bit of paranoia in this insane world we live in...

---

### Post by /etc/init.d/ on 2008-05-20
> **GeneralCody said:**
> My thread was about erasing files securely on a journaled file system, not about encryption, what so ever.
And your method still doesn't go any sort of length to delete files securely at all.  Writing zeroes to a file then syncing the disk doesn't magically bypass the journal.  When the file was written originally, portions of it may well have entered the journal.  

You also haven't taken into consideration reallocated sectors in the drive, or the fact that sensitive data relating to the file might exist in off-track areas, which no software utility can access or erase.  

Yet another thing to consider is the fact that the file was probably used at some point, meaning portions of it would have been in memory and potentially swapped to disk on another partition entirely.  

Some applications take backups and store them in /tmp, others create temporary or "working" files which will also leak data relating to the original file.

If you've printed the file at some point, some of the data may have been stored on-disk by the spooler, and leaked that way.

I could go on and on...

Point is.  If you want to securely erase data, wipe it using the drive's built in ATA Security Erase, and then throw it in an incinerator.  Or just the latter if you're not paranoid like me.  Else you're just kidding yourself.

---

### Post by GeneralCody on 2008-05-20
I see. I understand that your knowledge of computer security extends mine. That was partially why I posted this in the first place, to get reasonable responses, like the last one you wrote.

I still think that using a bootable CD, like [DBAN]("http://dban.sourceforge.net/"), to nuke the disk, before using it again, should suffice, don't you? If not, why not?

Or is the only option to actually de-magnetize the disk, and use a hammer or something like that, and buy a new one the only way?

Thanks for your last response, the former got me feeling like you were trying to make me look like an idiot. :-(

---

### Post by jdong on 2008-05-20
> **GeneralCody said:**
> 

I still think that using a bootable CD, like [DBAN]("http://dban.sourceforge.net/"), to nuke the disk, before using it again, should suffice, don't you? If not, why not?

Or is the only option to actually de-magnetize the disk, and use a hammer or something like that, and buy a new one the only way?

Thanks for your last response, the former got me feeling like you were trying to make me look like an idiot. :-(

It depends on who you're hiding from. I've got some buddies in the forensic data recovery business, and basically from what they've told me, throw enough man-hours and dollars at him, he can recover ANY mutilated disk (smashed to bits, wiped 1000 passes, etc) short of a disk heated to the Curie point.

Of course, after X number of wipe passes, you're talking about this being a multi-billion dollar, several month project, or more, which is entirely out of practicality for everything short of a strong governmental agency... If you're selling an old hard drive on eBay that used to contain some personal information, a nuke/wipe pass is more than plenty. If you're hiding stuff from the US government... well... good luck with that.

---

### Post by hyper_ch on 2008-05-20
What does that buddy then recommend? full disc encryption? Massive amounts of ram?

---

### Post by /etc/init.d/ on 2008-05-20
> **GeneralCody said:**
> I still think that using a bootable CD, like [DBAN]("http://dban.sourceforge.net/"), to nuke the disk, before using it again, should suffice, don't you? If not, why not?
DBAN is nice for overwriting host-accessible data areas.  However, DBAN won't/can't wipe reallocated sectors, the areas that are off-track, the host-protected area, and the extra information (such as error correcting codes) stored for each sector of the drive.  All these areas can potentially contain data, so that's a lot of information that you just can't wipe with DBAN.

A tool such as HDDErase, which invoke the ATA Security commands, would be a better choice, since these are supposed to wipe these areas in addition to user data.

> **GeneralCody said:**
> Or is the only option to actually de-magnetize the disk, and use a hammer or something like that, and buy a new one the only way?
According to governmental agencies, yes.  No standard ever advocates re-using a device that has been used to store top secret data.  In such cases, the devices are always physically damaged.

---

### Post by GeneralCody on 2008-05-20
> **jdong said:**
> It depends on who you're hiding from. I've got some buddies in the forensic data recovery business, and basically from what they've told me, throw enough man-hours and dollars at him, he can recover ANY mutilated disk (smashed to bits, wiped 1000 passes, etc) short of a disk heated to the Curie point.

Of course, after X number of wipe passes, you're talking about this being a multi-billion dollar, several month project, or more, which is entirely out of practicality for everything short of a strong governmental agency... If you're selling an old hard drive on eBay that used to contain some personal information, a nuke/wipe pass is more than plenty. If you're hiding stuff from the US government... well... good luck with that.

Actually, I'm not hiding anything from anyone, but I need some info on this subject for my exam in computer security, so thanks for sharing some knowledge.

---

### Post by jdong on 2008-05-20
> **hyper_ch said:**
> What does that buddy then recommend? full disc encryption? Massive amounts of ram?

If you want to be absolutely certain data on a magnetic medium is irrecoverable, you want to raise it to the curie point... Get a big pile of charcoal or a proper incinerator and have a BBQ.

---

