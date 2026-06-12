---
title: "File system security"
date: 2006-05-03
forum: Server Platforms
---

### Post by yusufm on 2006-05-03
Since anyone who has physical access to the box can get root through rebooting in single user mode, is there an easy automated way to encrypt the filesystem in ubuntu?
Thanks.

---

### Post by 23meg on 2006-05-03
You may want to set up a root password with ```
sudo passwd root
``` so that the system will ask for a password when booting in recovery mode. Note that this has disadvantages, widely discussed elsewhere on the forums.

---

### Post by yusufm on 2006-05-04
but when you boot in single user mode, it does not ask you for a password, it logs in as root automatically.

---

### Post by LordHunter317 on 2006-05-04
It's a useless measure anyway.  I can rescue CD bypass it in 30 seconds.

---

### Post by yusufm on 2006-05-04
I'm extremely surprised that this whole issue hasn't been addressed more actively. I guess it wasnt' really an issue when unix was run on mainframes in computer rooms, but today, having linux anywhere is extremely easy to get into, without recompiling the kernel or something.

---

### Post by LordHunter317 on 2006-05-04
[QUOTE=yusufm]I'm extremely surprised that this whole issue hasn't been addressed more actively.[/quote]Why?  What is the purpose?  If I have physical access the game is over anyway.

Encryption isn't a viable general purpose solution yet.  It's difficult to configure, can't be used in unattended scenarios (e.g., servers) and frequently degrades performance unacceptably.

> but today, having linux anywhere is extremely easy to get into, without recompiling the kernel or something.That's true of any operating system where I have phyiscal access.

---

### Post by yusufm on 2006-05-04
should atleast make it harder than rebooting the machine, or mounting the drive. If the persone was not necessarily out to get the information on the laptop, then if there was some good security on it, they would bother, but if all you personal information is just lyign there, why wouldn';t they use it.

---

### Post by LordHunter317 on 2006-05-04
[QUOTE=yusufm]should atleast make it harder than rebooting the machine, or mounting the drive.[/quote]Why?  It's not any harder to do the actiosn beyond that.  I reboot the machine and boot off a rescue CD.  then what password you set is totally irrelevant.

> If the persone was not necessarily out to get the information on the laptop,Then why are they attacking it?  This is a specious scenario.

> then if there was some good security on it, they would bother, but if all you personal information is just lyign there, why wouldn';t they use it.
IF the attacker isn't competent enough to know how to boot a rescue CD they're not competent enough to know how to boot in single-user mode, either.

---

### Post by yusufm on 2006-05-04
They could just be stealing the laptop, so why make it any easier for them. Also, if the filesytem was encrypted, we wouldn't need to be worried about booting in single user mode or from rescue disks.

[QUOTE=LordHunter317]Why?  It's not any harder to do the actiosn beyond that.  I reboot the machine and boot off a rescue CD.  then what password you set is totally irrelevant.

Then why are they attacking it?  This is a specious scenario.


IF the attacker isn't competent enough to know how to boot a rescue CD they're not competent enough to know how to boot in single-user mode, either.[/QUOTE]

---

### Post by LordHunter317 on 2006-05-04
[QUOTE=yusufm]They could just be stealing the laptop, so why make it any easier for them.[/quote]***That's the entire point: you are not in any way, shape, or form making it harder for them.***

Any password measure is senseless.  Encrpytion does wokr, but at a farily massive cost that's jsut not worth paying most of the time.

>  Also, if the filesytem was encrypted, we wouldn't need to be worried about booting in single user mode or from rescue disks.Right, which isn't setting a root password for single-user mode.  And like I said, isn't fesible in enough situations that it's presently senseless to do it OOB.

---

### Post by yusufm on 2006-05-04
If you had an encrypted file system, it _would_ be harder for people to get your data as opposed to having the files just sitting there on the disk for them to see.

Having an encrypted file system is wholly feasible and easy to use if it were designed into the OS. Just because it hasn't been done does not mean its not a good idea.

[QUOTE=LordHunter317]***That's the entire point: you are not in any way, shape, or form making it harder for them.***

Any password measure is senseless.  Encrpytion does wokr, but at a farily massive cost that's jsut not worth paying.

Right, which isn't setting a root password for single-user mode.  And like I said, isn't fesible in enough situations that it's presently senseless to do it OOB.[/QUOTE]

---

### Post by LordHunter317 on 2006-05-04
[QUOTE=yusufm]If you had an encrypted file system, it _would_ be harder for people to get your data as opposed to having the files just sitting there on the disk for them to see.[/quote]Yes, I said that.  What I said was any other measure is by and large pointless.

> Having an encrypted file system is wholly feasible and easy to use if it were designed into the OS.No, it isn't.  It cannot be securely done for unattended machines without a very complicated network infrastructure: you'd have to net boot the operating system to a point to where they could retreive the encryption key and decrypt the disk.  It's not acceptable anywhere CPU load is an issue.

> Just because it hasn't been done does not mean its not a good idea.It hasn't been done for whole harddrives at the OS level because it's almost totally nonsensical to do it that way.  You take too much of a performance hit for no gain.  Usually the amount of data that really needs to be encrypted is totally negligible.  AS such, mechanisms to encrypt files are usually more sensible.

It makes no sesnse to encrypt all of /usr, for example.  Most of /home is equally applicable.

---

### Post by 23meg on 2006-05-04
What it comes down to is that possible physical security flaws aren't meant to be reinforced with software security precautions, and vice versa.

---

### Post by ice60 on 2006-05-05
hi, there are two programs in synaptic which say they are transparent which means they are unseen by the person using the computer - CFS and cryptofs. i've used transparent encryption in the past with no problems you just have to make sure you remember your login password. the only draw back i know of is making backups of encrypted FSs.

---

