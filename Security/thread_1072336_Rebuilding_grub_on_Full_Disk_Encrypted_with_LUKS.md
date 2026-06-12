---
title: "Rebuilding grub on Full Disk Encrypted with LUKS"
date: 2009-02-17
forum: Security
---

### Post by cashmoney on 2009-02-17
So I accidentally wrote over grub when trying to install Sabayon (another flavor of linux).  Considering this was my work laptop I needed to get it up and running.  For anyone who finds themselves in the same situation the following steps are how I fixed mine.

Insert Ubuntu alt cd and select repair.  Type in your LUKS paraphrase and get to the point where you can run a shell on your root partition.


Next do:
 
```
cd /dev/mapper
```
Take not of the encrypted patition.  Mine was sda5_CRYPT.

next type 
```
grub
```
This allows you to run configuration commands in grub

Next do a 
```
device (hd0) /dev/mapper/<ENCRYPTED_PARTITION_NAME>
```

For example mine was device (hd0) /dev/mapper/sda5_CRYPT

next do a ```
find /boot/grub/stage1
```

This "should" find the stage 1 loader for linux. Take note of the output Mine was "(hd0,4)"

next do a 
```
root <output of previous command>
```

My case is was "root (hd0,4)"

next do 
```
setup (hd0)
quit
```

Finally do a 
> update-grub

You may get prompted to redo menu.lst 


Mine follows below
```

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-23-generic root=/dev/mapper/nate--lap-root ro quiet splash
initrd		/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-23-generic root=/dev/mapper/nate--lap-root ro single
initrd		/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet
```

---

### Post by Tubes6al4v on 2009-02-17
Thank You for writing this. I know I have gotten stuck at this before and ended up backing up the data and re-installing. Might I suggest appending "How-to:" to the begining of your title. That way people will find it easier.

---

### Post by cashmoney on 2009-02-18
> **Tubes6al4v said:**
> Thank You for writing this. I know I have gotten stuck at this before and ended up backing up the data and re-installing. Might I suggest appending "How-to:" to the begining of your title. That way people will find it easier.

Good Idea.
:popcorn:

---

### Post by newgen23 on 2011-07-12
Ok, after this forum erased my first comment because it was "too short", i will give it a second attempt.

I get an error on the command: find /boot/grub/stage1
Error: "Unknown partition type signature"
Error 15: File not found

Ok, i admit that the update from ubuntu 10.10 to 11.04 did not only mess up my system, but also removed my grub folder -> this ubuntu already feels like windows...

How can I recreate the stage1 file? And why does it say "Unknown partition type signature" ?

/dev/mapper/sda4_crypt is my crypt fs, which can be mounted with cryptsetup without any problems.

And why does everyone on the irc channel say "install ubuntu new" ? thats no way to solve problems. thats how microsoft does it.

UPDATE:
ok, stage1 is in place. grub is still unable to read the correct partition type. it seems grub is unable to understand that /dev/sda4 is my crypto partition.

---

