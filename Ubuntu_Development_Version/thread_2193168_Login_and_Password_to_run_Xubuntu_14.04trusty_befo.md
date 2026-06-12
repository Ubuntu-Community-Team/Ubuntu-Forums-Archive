---
title: "Login and Password to run Xubuntu 14.04/trusty before installing?"
date: 2013-12-11
forum: Ubuntu Development Version
---

### Post by NTL2009 on 2013-12-11
I searched, and could not find an answer to what should be obvious, but...

Today, I DL'd the Xubuntu version of trusty-desktop-i386.iso from 

here: [http://cdimage.ubuntu.com/xubuntu/daily-live/20131211/trusty-desktop-i386.iso](http://cdimage.ubuntu.com/xubuntu/daily-live/20131211/trusty-desktop-i386.iso)

I was able to get it on a 4GB USB thumb drive, using Unetbootin, and it boots OK to my little ASUS EEE PC901. But when I choose "Try Xubuntu w/o Installing', it asks for a name and password.

Do I need to sign up as a tester to get a password? I didn't see anything about this. Or is my install hosed? MD5SUM was good on the downloaded iso.

TIA -NTL2009

---

### Post by NTL2009 on 2013-12-11
Geez, ten seconds later I found it! I can mark my own thread solved! This might help someone else. (Why don't they put this in the notes?)[URL="https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1259525"]

https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1259525[/URL]

For Xubuntu, the username seems to be "xubuntu", no password.

-NTL2009

---

### Post by Elfy on 2013-12-11
> **NTL2009 said:**
> Geez, ten seconds later I found it! I can mark my own thread solved! This might help someone else. (Why don't they put this in the notes?)[URL="https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1259525"]

https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1259525[/URL]

For Xubuntu, the username seems to be "xubuntu", no password.

-NTL2009

It's not in the notes - because it's a bug - it's not setting the session properly.

---

### Post by NTL2009 on 2013-12-11
> **Elfy said:**
> It's not in the notes - because it's a bug - it's not setting the session properly.

Ahh, I see. I saw some older references to it, so I thought maybe it was reported as a bug recently, but something that was actually intended.

So I guess it is an old bug that crept in again. Probably just a set-up error when they build it?

-NTL2009

---

### Post by zbeckerd on 2014-04-03
LUbuntu is same
lubuntu = uname
no psswd

---

