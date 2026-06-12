---
title: "Trace sweeper?"
date: 2008-06-17
forum: Security
---

### Post by primky on 2008-06-17
I would need a program, similar to this:

> Description
This utility helps to clean unwanted traces the user leaves on the system. 

[http://linuxappfinder.com/package/sweeper]("http://linuxappfinder.com/package/sweeper")

But it says it's for KDE. Does anyone know any similar software?
I have Ubuntu Hardy 8.04 with Gnome.

---

### Post by primky on 2008-06-17
Cmon.. Don't you people use anything like this?

---

### Post by noerrorsfound on 2008-06-17
You can usually use KDE programs in GNOME. They just look different because they use Qt.

---

### Post by primky on 2008-06-18
Well, it doesn't work fully in Gnome.

Does anyone know any similar program? I need it do delete for example history of opened files etc...

---

### Post by hyper_ch on 2008-06-18
> **primky said:**
> Cmon.. Don't you people use anything like this?

I have a fully encrypted system so I don't have think about what I need to delete and secure and and and.... except from /boot everything is secured...

---

### Post by primky on 2008-06-19
Ok, i also would like to have Linux system encrypted.
But i have Win XP on another partition, so the whole disk cannot be encrypted.
I know True Crypt, but when i wanted to encrypt only partition D:/ it said all data will be erased, lol.

Any n00b tutorial for this?

---

### Post by hyper_ch on 2008-06-19
> **primky said:**
> Ok, i also would like to have Linux system encrypted.

it's not the whole disk but the whole system in linux.

---

### Post by primky on 2008-06-19
Do you know any noob friendly tutorial on how to do this?

---

### Post by hyper_ch on 2008-06-19
simplest thing would be to install with the alternate cd and select encrypted lvm from there ;)

---

### Post by primky on 2008-06-19
But i already have installed Ubuntu and i don't want to reinstall.

Here is the whole story:

I have these partitions
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        9964    39078112+   f  W95 Ext'd (LBA)
/dev/sda5            5100        7983    23165698+   7  HPFS/NTFS
/dev/sda6            7984        9875    15197458+  83  Linux
/dev/sda7            9876        9964      714861   82  Linux swap / Solaris


I want to encrypt all partitions where linux is on. What program do i need and is there any tutorial for this?

---

### Post by Nullack on 2008-06-19
A gnome version of ccleaner would be great

---

### Post by hyper_ch on 2008-06-19
well, those partitions that you want to encrypt with luks/dm_crypt have to be cleaned anyway

---

### Post by waggingwabbit on 2008-06-19
does encrypting the partition lower performance alot? or in anyway at all?

---

### Post by hyper_ch on 2008-06-19
it does... it has to encrypt/decrypt all data read and written from it... however I don't notice it except when I'm moving large files around.

---

