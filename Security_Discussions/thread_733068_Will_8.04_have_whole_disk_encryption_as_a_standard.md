---
title: "Will 8.04 have whole disk encryption as a standard option?"
date: 2008-03-23
forum: Security Discussions
---

### Post by nutz on 2008-03-23
I have been searching around on this and haven't found a conclusive answer one way or the other. Will 8.04 include whole disk encryption as a standard option?

---

### Post by kevdog on 2008-03-23
Good question -- I wish it would at least as an option on the standard install in addition to the alternative disk.

---

### Post by nutz on 2008-03-23
> **kevdog said:**
> Good question -- I wish it would at least as an option on the standard install in addition to the alternative disk.


+1

I remember reading a while back that this feature was intended to be available with 8.04 but sadly I can't find any documentation on it and the fact that they don't expressly mention it in the new features list has me doubting that it will be available.

Has anyone come across any information on this feature? Did they scrap it during the developement?

---

### Post by thewanderer on 2008-03-24
Whole disk encryption on install would definitely be yet another reason to get people to make the switch to Ubuntu.

[Truecrypt]("http://www.truecrypt.org") is an excellent package for those who havent used it before - it will allow you to encrypt a partition or create an encrypted partition within a file. This is excellent for storing documents or other sensitive data.

As far as I know there is no full disk encryption (of Operating System) option for Linux with TrueCrypt as yet.

---

### Post by klopa3333 on 2008-03-24
@ thewanderer: Correct, truecrypt WDE does not work on Ubuntu.

Here [http://www.tuxmachines.org/node/25102](http://www.tuxmachines.org/node/25102) they say that 8.04 standard will not have the WDE option. Only the alternative install CD will have it.

Here's a good guide for setting up WDE through the alternative install CD:
[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

---

### Post by nutz on 2008-03-25
> **klopa3333 said:**
> @ thewanderer: Correct, truecrypt WDE does not work on Ubuntu.

Here [http://www.tuxmachines.org/node/25102](http://www.tuxmachines.org/node/25102) they say that 8.04 standard will not have the WDE option. Only the alternative install CD will have it.

Here's a good guide for setting up WDE through the alternative install CD:
[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

That guide you posted worked like a charm. I think it could be easier so more people could do it but otherwise it gets the job done. I am going to ask the mods to make a sticky to that guide.

---

### Post by wieman01 on 2008-03-26
From Kubuntu's website:

[https://wiki.kubuntu.org/HardyHeron/Beta/Kubuntu]("https://wiki.kubuntu.org/HardyHeron/Beta/Kubuntu")
> **Encryption**

**Info: EncryptedFilesystemsInstaller**

For the first time ever, you can encrypt your file system (all but the /boot partition) for increased security during the installation of Kubuntu. Simply select the encryption option at the portion of the installation that requires you to setup your hard drive partitions. This option is only available with the Alternate Install CD at this time. 

---

