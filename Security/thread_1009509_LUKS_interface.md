---
title: "LUKS interface"
date: 2008-12-12
forum: Security
---

### Post by trekvarten on 2008-12-12
Hi,
I've got this minor inconvenience with my LUKS-based disk encryption system.

Here's the setup:
1. I have a LVM+LUKS combo for the most important directories (/home, /var and so on) with password1, working just fine
2. I have another partition (LUKS on an internal physical volume) for storing sensitive files with password2, however it doesn't get used that often.

The thing is: I'm currently using /etc/crypttab for both of these partitions, which of course makes cryptdisks ask for both passwords on every boot, and since the computer gets restarted quite frequently, it is a pain having to type both passwords every time (because partition 2 isn't needed most of the time).
Also, I don't want partition 2 to stay unlocked in case someone reaches the computer while it is turned on and extracts the key from RAM.

So, what I'm looking for is some easy way to mount the second partition on demand. An easy task you say; and indeed I've found it to be quite trivial with scripts for mounting and unmounting etc. What I'm looking for, however, is a more elegant, intuitive and secure solution; I'm thinking of the way GNOME reacts to LUKS-encrypted external drives:
It identifies the drive as encrypted, asks for a password when it is inserted, and unlocks + mounts; if no password is given, the drive can still be reached from Places... and most importantly, it closes the encrypted drive after it's unmounted. However, this doesn't seem possible with internal drives for some reason probably related to requiring root access to access the device.

I've messed a bit with fstab options etc, no dice.

The ideal solution would be to as a normal user be able to mount the volume like any external drive, just asking for the encryption password, in GNOME.

Any ideas? :p

---

### Post by Colt45 on 2008-12-31
GDecrypt

Says it supports mounting LUKS partitions, I haven't tested though.

[http://gdecrypt.pentabarf.de/](http://gdecrypt.pentabarf.de/)
[https://launchpad.net/gdecrypt](https://launchpad.net/gdecrypt)
[https://launchpad.net/ubuntu/+source/gdecrypt](https://launchpad.net/ubuntu/+source/gdecrypt)

---

### Post by hyper_ch on 2009-01-01
why not unlock the second one automatically with a keyfile that's stored on the first harddisk... so yo ahve to unlock that one and automatically the second one will be unlocked to.

---

### Post by RansomStark on 2009-01-02
I had the same problem, my main drive is RAID1+LUKS, but I had another drive which I use as a backup for my most important files, obviously I wanted to encrypt the data to keep it safe on the backup drive. So, I used truecrypt in the end. It has a GUI interface and allows for casual mounting/unmounting of the drive as and when required. The handy part is truecrypt drives work with both linux and windows so in the event of a system failure I can access my files from a windows PC.

[http://www.truecrypt.org/](http://www.truecrypt.org/)

You can download a deb package from

[http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

Hope this helps!

---

### Post by Colt45 on 2009-01-03
> **RansomStark said:**
> I had the same problem, my main drive is RAID1+LUKS, but I had another drive which I use as a backup for my most important files, obviously I wanted to encrypt the data to keep it safe on the backup drive. So, I used truecrypt in the end. It has a GUI interface and allows for casual mounting/unmounting of the drive as and when required. The handy part is truecrypt drives work with both linux and windows so in the event of a system failure I can access my files from a windows PC.

[http://www.truecrypt.org/](http://www.truecrypt.org/)

You can download a deb package from

[http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

Hope this helps!

You can access LUKS volumes on windows via FreeOFTE.  The LUKS volume will need to have been originally formatted with a Fat32/ext2/ext3 filesystem.  Fat32 is natively supported by windows.  ext2/ext3 have third party drivers available for windows.

[http://www.freeotfe.org/](http://www.freeotfe.org/)

---

### Post by bluesceada on 2009-03-22
Anyone got FreeOTFE working together with the ext2 IFS driver?
I tried different (though not all) versions of both and couldn't succeed. I also can't find much on google, just someone for whom it just worked.

I have a working ext2 ifs driver from fs-driver.org running, which is able to access unencrypted volumes.
Then I install FreeOTFE and do: File > Linux-Volume > Mount partition

When deselecting the "Base IV cypher on hash length" option it says it is unable to mount the partition/volume.
When keeping it selected, FreeOTFE succeeds, but when I try to access the drive from Windows Explorer, it says it isn't formatted.
I also can't see it from within the ext2 ifs settings.

My partition/volume has:
Cipher name:    aes
Cipher mode:    cbc-essiv:sha256
Hash spec:      sha1
and it has one passphrase-key in slot 0

I definately want to get this working with ext3.

Anyone can help?

// edit: Oh, and we are talking about Win XP SP3

// edit2:

Maybe solved it (didn't test it so far): The ext2/3 Filesystem has to be created with inode size of 128 bytes! Just recently the default has become 256bytes (for whatever reason), which probably causes the problem.

---

### Post by jmcantrell on 2009-03-23
Did changing the inode size fix the problem? I'm having the exact same issue with a recently formatted drive, and would like to know if this worked for you.

---

### Post by jmcantrell on 2009-03-24
Update: Changing the inode size from 256 to 128 fixed the issue. I had an identical drive that I formatted about a year ago, and it worked correctly. I guess the defaults changed recently.

---

### Post by bluesceada on 2009-05-04
Oh sorry, I wanted to report back...

Yes, changing the inode size did solve the problem. I hope the ext2/3 windows driver will someday become an update for any inode size.

But so far this is good :-)

And yeah, the defaults changed, because now some more data can be stored directly in the inodes (extended attributes, access control lists, ..)
And for ext4 this is also the default inode size.

---

