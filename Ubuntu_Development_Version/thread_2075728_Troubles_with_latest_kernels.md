---
title: "Troubles with latest kernels"
date: 2012-10-24
forum: Ubuntu Development Version
---

### Post by dino99 on 2012-10-24
](*,)   dont hard reset your ext4 system

EXT4 Data Corruption Bug Hits Stable Linux Kernels  ( 3.2 -> 3.6 )

[http://www.phoronix.com/scan.php?page=news_item&px=MTIxNDQ](http://www.phoronix.com/scan.php?page=news_item&px=MTIxNDQ)

it seems that 3.7 is not affected, but not sure, as that commit is not yet fixed nor removed.

---

### Post by ventrical on 2012-10-24
Thanks for the warnings.

---

### Post by grahammechanical on 2012-10-24
Makes me glad that my /home partition is still ext3. Sometimes a hard reset is the simple way out of messed up login screen or desktop, such as we got a few weeks ago.

> So it will only show up if the system has been rebooted twice in fairly quick succession.

Not got much choice when trying to get to a working desktop. 

Regards.

---

### Post by zika on 2012-10-25
Is liquorix 3.6 affected?

---

### Post by dino99 on 2012-10-25
> **zika said:**
> Is liquorix 3.6 affected?

liquorix or not liquorix, where is the difference ?

---

### Post by zika on 2012-10-25
> **dino99 said:**
> liquorix or not liquorix, where is the difference ?Just the question I've asked...

---

### Post by JMB74 on 2012-10-25
> **zika said:**
> Is liquorix 3.6 affected?

Looking at the sources and configs, the 3.6 in their debian repos seems to be based on linux 3.6.2 or 3.6.2?

So yes, presumably they would be effected?

But also see: [http://www.h-online.com/open/news/item/Stable-Linux-kernel-hit-by-ext4-data-corruption-bug-Update-1736110.html](http://www.h-online.com/open/news/item/Stable-Linux-kernel-hit-by-ext4-data-corruption-bug-Update-1736110.html)

> Theodore Ts'o has continued his investigation of the bug and has found that the problem was more [esoteric]("http://thread.gmane.org/gmane.linux.kernel/1379725/focus%3D34994") than was first thought. The user who reported the problem was using umount -l, which immediately unmounts the filesystem without waiting for it to stop being busy. The bug is now [thought]("http://thread.gmane.org/gmane.linux.kernel/1379725/focus%3D35003")  to be caused when the machine is being shut down while it is in the  process of unmounting the filesystem with an already compromised  journal.

 The developers are [still working]("http://thread.gmane.org/gmane.linux.kernel/1379725/focus%3D35006")  to pinpoint the exact problem and it might actually involve more kernel  components than just the ext4 drivers. [COLOR=Red]In any case, it has become clear  that the bug needs a very specific configuration to surface and is  unlikely to affect most users.[/COLOR]


---

### Post by dino99 on 2012-10-25
Generally speaking its a problem for all the journalling systems around there. So the problem is real when the system suddenly fail: hardware issue, power cut down, ...

note: i was lazy to upgrade my /home from ext3 to ext4, but now im very happy to still use ext3 on /home, i feel better secured.

---

### Post by Starks on 2012-10-25
This could be a huge problem during the first major breakage.

---

### Post by dino99 on 2012-10-26
Feedback

Problem has been narrowed down, and should not affect average users.


*****
One of the users who ran into problems were using experimental new features that are not enabled by default. We can't stop users from trying out new features that aren't enabled by default. Things like metadata checksums are not enabled by default specifically because they aren't ready yet.
*****

So its a no problem, but a huge buzz :confused:

---

### Post by zika on 2012-10-26
> **dino99 said:**
> Feedback

Problem has been narrowed down, and should not affect average users.


*****
One of the users who ran into problems were using experimental new features that are not enabled by default. We can't stop users from trying out new features that aren't enabled by default. Things like metadata checksums are not enabled by default specifically because they aren't ready yet.
*****

So its a no problem, but a huge buzz :confused:Will it be solved until 20.12. 2012. ... ;)?

---

### Post by bailout on 2012-10-29
Does anyone know whether this affects the 12.10 kernel?

I have just installed kubuntu 12.10 and had put Bodhi on another partition. I started getting error messages on the Bodhi install that it couldn't write to files and the install soon wouldn't boot.

I thought it was just a problem with Bodhi and sonething I had done to it but I am now getting the similar problems start with Kubuntu. I know Bodhi is based on 12.04 but uses updated kernels.

I have been rebooting a lot going between the installs and need to decide whether it could be this kernel bug or whether my hd is failing.

thanks

---

### Post by ventrical on 2012-10-29
> **bailout said:**
> Does anyone know whether this affects the 12.10 kernel?

I have just installed kubuntu 12.10 and had put Bodhi on another partition. I started getting error messages on the Bodhi install that it couldn't write to files and the install soon wouldn't boot.

I thought it was just a problem with Bodhi and sonething I had done to it but I am now getting the similar problems start with Kubuntu. I know Bodhi is based on 12.04 but uses updated kernels.

I have been rebooting a lot going between the installs and need to decide whether it could be this kernel bug or whether my hd is failing.

thanks

 How old is your hdd,? (check smart info in disk utility). Through time older hdds increase their wattage drain and can put a drain on the power-supply. In contradistinction, older power supplies loose their wattage output gradually over time. These two factors can emulate a software bug/fail.

---

### Post by bailout on 2012-10-29
I ran the hd manufacturers (WD) disk check utility and both the quick and extended tests showed no errors with the hd.

---

