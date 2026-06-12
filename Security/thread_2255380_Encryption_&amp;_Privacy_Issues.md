---
title: "Encryption &amp; Privacy Issues"
date: 2014-12-04
forum: Security
---

### Post by buntuluxx on 2014-12-04
Hey Guys!

I run three partitions, 2 with Windows 8.1 and one with Ubuntu14.04.

1.)Since I am very concerned with privacy I would like to know if there are any standardized or pre-configured functionalities within Ubuntu14.04, which could indicate information regarding mounted volumes, opened/general file history, other privacy concerns and how to turn them off or hinder them from doing so.


Thanks

---

### Post by mastablasta on 2014-12-05
1. first you need to remove yourself from internet. as long as you are online we can see your IP from that various other data. :P
from the question you posted I am not sure you understand the privacy concept. if the OS is logging any errors the user experiences this is not a privacy breach. if the os is reporting your name, phone number etc to the internet that is privacy issue.

2. there is no way to configure Linux partition in windows. Ubuntu install allows encryption of Home folder which is where your personal data is.  again encrypted disk partitions or disks protect the data if the disk is stolen. they do not offer any privacy protection. for example if you are logged into your computer and someone hack into it or monitors your activity the will see you encrypted data.

otherwise have a look at Tails or Liberte Linux.

---

### Post by buntuluxx on 2014-12-05
Sarcastic and unhelpful.

---

### Post by sudodus on 2014-12-05
I don't think the intention of the post is to be sarcastic and unhelpful. There might be a language barrier, that at least one of you is not a native English speaker. There might also be a barrier because of the technical language used. (By the way, my native language is *not* English.)

Anyway,

- Are you concerned about attacks via the internet or attacks from people who have physical access to the computer (for example thieves or colleagues)? Or both?

- Is it a laptop or a desktop computer?

- Could you consider keeping the Ubuntu system in a separate drive (a second internal drive or an external drive, for example a big and fast USB 3 pendrive)?

- Is the Ubuntu installation a WUBI install, or a regular dual install alongside Windows?

---

### Post by buntuluxx on 2014-12-05
A language barrier?;)

What gives you the impression, that I am not a native?

Shared flat situation.

Only one SSD, that has been partitioned with PM.

But please concentrate on the first question, which I consider to be of primary concern in this matter

---

### Post by lisati on 2014-12-05
> **buntuluxx said:**
> A language barrier?;)

What gives you the impression, that I am not a native?

:lolflag:

This is an international forum. English is a second language for many of the forum members. Even among the members for whom English is their native tonuge there are regional differences that can sometimes trip up the unwary.

In my opinion, which should not necessarily be taken as representative of other forum staff,  mastablasta provided a good response earlier in this thread.

---

### Post by sudodus on 2014-12-05
I conclude that you are concerned about attacks via the internet ***as well as*** attacks from people who have physical access to the computer (for example thieves or colleagues).

I don't know any good method to get full encryption of the Ubuntu partition, when the drive is shared with another operating system. There is encryption of the home directory, which is possible in this case, but encrypted LVM will grab the whole drive.

This does not mean that there is no suitable method, only that I have no method to recommend, except to run ***Ubuntu from an external drive***, or to run some other linux distro, for example ***Tails***, which was mentioned by mastablasta. (Tails is made to run as a live system (from an external drive). See [this link]("https://tails.boum.org/"))

If you find Tails too difficult to use, maybe you can get enough privacy/security with Ubuntu and encrypted home using the tips in the following link

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

