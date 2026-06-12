---
title: "erase memory"
date: 2008-03-28
forum: Security Discussions
---

### Post by cdenley on 2008-03-28
Is it possible to erase the memory on shutdown? I know you could run the memory tester, but that's not very convenient. Could you do this with an init script? If so, which script, halt? Could you overwrite memory with a command like this...?
```

dd if=/dev/zero of=/dev/mem bs=1 conv=noerror,sync

```
Obviously it couldn't erase all memory, since the script itself and dd would have to be loaded into memory, but would it skip over memory it can't write to and overwrite all unused memory? I tried it, and it would cause the system to segfault while shutting down. Maybe it's overwriting the kernel? Would I have to write a program that allocates memory until it can't allocate memory anymore. Is there a command that could do this? Would either method erase the swap partition? Would it erase an encryption key used for whole disk encryption?

---

### Post by finer recliner on 2008-03-28
if you do that command, you will surely overwrite the space the OS is using, which will make your system crash.


Why do you feel you need to wipe the memory on shutdown in the first place? Computer memory is not non-volatile. This means it loses any data stored there if the power is turned off (one of the big differences between a HDD and RAM).

---

### Post by Whiffle on 2008-03-28
> **finer recliner said:**
> if you do that command, you will surely overwrite the space the OS is using, which will make your system crash.


Why do you feel you need to wipe the memory on shutdown in the first place? Computer memory is **volatile**. This means it loses any data stored there if the power is turned off (one of the big differences between a HDD and RAM).

Fixed :)

---

### Post by cdenley on 2008-03-28
> **finer recliner said:**
> if you do that command, you will surely overwrite the space the OS is using, which will make your system crash.


Why do you feel you need to wipe the memory on shutdown in the first place? Computer memory is not non-volatile. This means it loses any data stored there if the power is turned off (one of the big differences between a HDD and RAM).

[http://citp.princeton.edu/memory/](http://citp.princeton.edu/memory/)
[http://ubuntuforums.org/showthread.php?t=736594](http://ubuntuforums.org/showthread.php?t=736594)

I guess it's a little paranoid to think that someone is going to steal your ram and dump it's contents minutes after you walk away from it, but I guess I'm curious and have too much time on my hands.

---

### Post by finer recliner on 2008-03-29
the most important thing to realize is, if someone has physical access to your computer, there will always be a way for them to get your personal data. 

some methods like encrypting the HDD and password protecting the BIOS will slow a malcious person down, but with enough time and energy, someone will always be able to get to your data. :-/

---

### Post by pietjanjaap on 2008-03-30
There is a website that has a program that can wipe, memory and swap, so if you use a program that leaves traces, you can wipe it.



[http://www.techthrob.com/tech/securedelete.php](http://www.techthrob.com/tech/securedelete.php)

Command  	Function
srm ,	  Secure remove; used for deleting files or directories currently on your hard disk;
smem, 	Secure memory wiper; used to wipe traces of data from your computer's memory (RAM);
sfill, 	      Secure free space wiper; used to wipe all traces of data from the free space on your disk;
sswap, 	 Secure swap wiper; used to wipe all traces of data from your swap partition.

---

### Post by hyper_ch on 2008-03-31
> **finer recliner said:**
> the most important thing to realize is, if someone has physical access to your computer, there will always be a way for them to get your personal data. 

some methods like encrypting the HDD and password protecting the BIOS will slow a malcious person down, but with enough time and energy, someone will always be able to get to your data. :-/

Sure there is, but with a strong encryption it just takes "a little" longer...

---

