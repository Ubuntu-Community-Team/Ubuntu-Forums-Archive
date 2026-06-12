---
title: "Encrpyt Single Partitions"
date: 2008-02-22
forum: Security Discussions
---

### Post by TorchlightJay on 2008-02-22
Hey all,

I was wondering if it's possible to encrypt single (or a few) partitions and if so, what tools would I use? I have seen a lot of tutorials for encrypting files and entire hard drives but I haven't seen much in terms of doing a single partition. I want to be able to create custom partitions and then encrypt them all individually, not just one fell swoop of the whole hard drive. Any ideas?

---

### Post by HermanAB on 2008-02-22
dm-crypt is the standard.

---

### Post by TorchlightJay on 2008-02-22
cool, can I use DM Crypt even after the partition is setup or is formating necessary? Is the partition bootable? can I mount and use it? Just curious.

---

### Post by euler_fan on 2008-02-22
Truecrypt has some capability in this regard as well.

---

### Post by TorchlightJay on 2008-02-22
Cool, which is better? Truecrypt or DM-Crypt? Is it more or less a "Pepsi & Coca-Cola" style argument or are there major differences?

---

### Post by euler_fan on 2008-02-22
I don't think for most things you're going to see a huge difference. I use Truecrypt because there are some files I have which are sensitive (like copies of bank account number, etc) but I don't feel a need to encrypt the entire disk. For this TrueCrypt excels.

The other thing would be if there is a particular feature you decide you need, for instance I think the consensus is that dm-crypt is better for whole disk encryption if such is even possible in Linux with TrueCrypt (I think it is in Windows, for instance).

Just remember: anyone with physical access to the machine while its running, some wits, and some technical savy can now get past your encryption using methods which have been [recently]("http://www.schneier.com/blog/archives/2008/02/cold_boot_attac.html") [disclosed]("http://www.freedom-to-tinker.com/?p=1257").

---

### Post by HermanAB on 2008-02-23
Crypto is complicated.  Happy reading:
[http://www.saout.de/misc/dm-crypt/](http://www.saout.de/misc/dm-crypt/)

---

