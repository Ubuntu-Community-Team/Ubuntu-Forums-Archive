---
title: "TrueCrypt Fails to Create Encripted Volume in Ubuntu 11.10"
date: 2011-10-15
forum: Security
---

### Post by IntoFlow on 2011-10-15
I've tried TrueCrypt 7.0a as well as 7.1. This problem occurs in Ubuntu 11.10.

When the volume size I want to create is around 10GB or above, after TC finishes encrypting, everything freezes and stays frozen. Nothing happens and I have to force shut down the computer. (I left it overnight once and it stayed frozen for hours - then I just shut it down.)

This issue did not occur in Ubuntu 11.04.

It's frustrating because I can't create a secure environment on my PC where I can store the files I want, and I need much more than 10GB.

When I want to encrypt around 300 MB, then it works...

Can anyone re-create this, or is this issue known about?

Thanks.

---

### Post by Rob_H on 2011-11-06
I started having the same problem since upgrading to 11.10. I fixed it by going to **Settings -> Preferences -> System integration** and then put a checkbox next to "Do not use kernel cryptographic services". I was also getting intermittent lock-ups when accessing encrypted volumes so I'm hoping this fixes that problem, too, but I haven't been testing long enough to say for sure. At least volume creation works now.

---

### Post by c.cobb on 2011-11-07
> **Rob_H said:**
> . . .put a checkbox next to "Do not use kernel cryptographic services".

Do you have the [dmsetup package]("http://packages.ubuntu.com/search?keywords=dmsetup") installed? If not, give that a try.

---

### Post by Rob_H on 2011-11-07
> **c.cobb said:**
> Do you have the [dmsetup package]("http://packages.ubuntu.com/search?keywords=dmsetup") installed? If not, give that a try.

Yeah, it is installed. Makes no difference I guess.

---

### Post by c.cobb on 2011-11-07
It used to make a difference. Maybe a defect came with with the upgrade, or something else has changed? 

Dunno much about device mapper, but in a wrapper script I wrote for TC, when the dmsetup command was not found, had to add the 'nokernelcrypto' mount option or the script wouldn't work.

---

### Post by fufyr4ik on 2011-12-21
I confirm the problem with Ubuntu 11.10. Hope, they'll fix it soon!

---

### Post by tubbygweilo on 2011-12-21
Has any of the posters who came across this problem described it to [LaunchPad]("https://bugs.launchpad.net/ubuntu?field.searchtext=+truecrypt&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")?

---

### Post by replicant.nz on 2012-01-11
> **Rob_H said:**
> I started having the same problem since upgrading to 11.10. I fixed it by going to **Settings -> Preferences -> System integration** and then put a checkbox next to &quot;Do not use kernel cryptographic services&quot;. I was also getting intermittent lock-ups when accessing encrypted volumes so I'm hoping this fixes that problem, too, but I haven't been testing long enough to say for sure. At least volume creation works now.

 Where do I find "Do not use kernel cryptographic services" with unity?

---

### Post by Rob_H on 2012-01-11
> **replicant.nz said:**
> Where do I find "Do not use kernel cryptographic services" with unity?

It's not in Unity. It's in the TrueCrypt GUI.

---

### Post by sh4d0w808 on 2012-01-12
Do you want to use fulldisk encryption?

---

