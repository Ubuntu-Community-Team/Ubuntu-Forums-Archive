---
title: "Encrypt whole partition after installion"
date: 2009-03-01
forum: Security
---

### Post by maimed on 2009-03-01
Hello,
I have searched around for a few guides but a lot of them require that you do it before you start using the partition otherwise all your programs will be deleted. Is there a way to encrypt my ubuntu partition without losing anything and also will this affect anything when i am using my ubuntu from day to day besides password at startup?
Thanks a lot

---

### Post by bodhi.zazen on 2009-03-01
No, you basically need to re-install as encryption is a destructive process, ie it destroys all data on the partition as part of the encryption.

---

### Post by maimed on 2009-03-02
hmmm ok cheers for that. Well then if i were to re-install and encrypt could i use something like clonezilla to backup everything and restore it while still having my encryption? Would this be any problem with backing up all the data and then restoring it to a new encrypted partition? 
And also what is the best guide out there to encrypting you partition with a decent encryption at least AES, can someone please link me to it. 
Thanks a lot

ps bodhi: i like your sig :)

---

### Post by Kobalt on 2009-03-02
Yes, you can save your data to some place and move it to your encrypted partition afterwards.
Want an encrypted /home partition ? [Check me out.]("http://www.nschirrer.com/encrypted-home-directory/")

---

### Post by bodhi.zazen on 2009-03-02
> **maimed said:**
> hmmm ok cheers for that. Well then if i were to re-install and encrypt could i use something like clonezilla to backup everything and restore it while still having my encryption? Would this be any problem with backing up all the data and then restoring it to a new encrypted partition? 
And also what is the best guide out there to encrypting you partition with a decent encryption at least AES, can someone please link me to it. 
Thanks a lot

ps bodhi: i like your sig :)

Thanks :redface:

clonezilla or partimage or similar will not work as they will over write your partition again.

As suggested by Kobalt , you need to copy the data to another partition or removable device, re-install, then restore the data.

---

### Post by maimed on 2009-03-07
Okay well i will prob screw around with this in the upcoming week lets just hope that i don't mess anything up is there a way to get all of my updates and all programs to work with new encrpted partition, sorry i am a bit of a noob

---

### Post by DGortze380 on 2009-03-07
> **maimed said:**
> Okay well i will prob screw around with this in the upcoming week lets just hope that i don't mess anything up is there a way to get all of my updates and all programs to work with new encrpted partition, sorry i am a bit of a noob

My suggestion is that, unless for some reason you have data sensitive enough to warrant hold disk encryption, you don't do it.

It is rather complex to backup, and if/when you lose the key, you data is gone. Period.

If you have a few items to protect, I suggest an encrypted virtual drive.

---

### Post by maimed on 2009-03-08
Yeah ok, i will just look at something like that then. Thanks a lot for all the input though guys appricated :)

---

### Post by Tubes6al4v on 2009-03-08
If you have the hard drive space, you could make another partition, install and encrypted FS on that, then copy your main Ubuntu partition over. This way you could "test drive" full disk encryption. All my linux stuff is encrypted, just in case. And there are not too many more steps to go through for backups.

---

### Post by hyper_ch on 2009-03-08
it is possible to encrypt the full system after installation but that involves having enough space to move things around while doing so. There is an article in C'T that explains how to do it on a debian system.

However I'd say it's simpler to do a fully encrypted reinstall.

---

### Post by mk4umha on 2009-03-23
How does one do a new install of Ubuntu releases when the partitions have already been encrypted? Is there any way to "upgrade" without destroying a /home or /share partition that's already encrypted?

---

### Post by bodhi.zazen on 2009-03-24
> **mk4umha said:**
> How does one do a new install of Ubuntu releases when the partitions have already been encrypted? Is there any way to "upgrade" without destroying a /home or /share partition that's already encrypted?

You can preserve partitions, but it is a hassle. 

IMO it is far easier to copy the data (to an encrypted partition or flash if you wish) and then restore the data.

This is how you do it manually : [http://ubuntuforums.org/showthread.php?t=1034910](http://ubuntuforums.org/showthread.php?t=1034910)

Hopefully with 9.04 the desktop CD will have some options for encryption or the alternate CD will do this more automatically (and offer ext4).

---

### Post by mk4umha on 2009-03-24
> **bodhi.zazen said:**
> You can preserve partitions, but it is a hassle. 

IMO it is far easier to copy the data (to an encrypted partition or flash if you wish) and then restore the data.

This is how you do it manually : [http://ubuntuforums.org/showthread.php?t=1034910](http://ubuntuforums.org/showthread.php?t=1034910)

Hopefully with 9.04 the desktop CD will have some options for encryption or the alternate CD will do this more automatically (and offer ext4).

Thanks for the quick response. I've decided to go the old school route for now with no encryption until 9.04.

---

