---
title: "Request: PwManager"
date: 2005-06-18
forum: Ubuntu Backports
---

### Post by Bob D. on 2005-06-18
*"A KDE password manager saves your passwords blowfish-encrypted in one file, so you have to remember only one master-password instead of all."*

[http://passwordmanager.sourceforge.net/index.html]("http://passwordmanager.sourceforge.net/index.html")

Basically a KDE-centric password manager similar in function to Revelation, the Gnome-centric password manager you so kindly backported. For various reasons, I've switched to Kubuntu (KDE 3.4.1) and would like to see if PwManager can be backported.

I found a repo for it (deb [ftp://ftp.real-time.com/linux/real-time]("ftp://ftp.real-time.com/linux/real-time") unstable custom) but there are some dependency problems. And they may be sticklers...to whit,

 ```
pwmanager:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
  Depends: libidn11 (>=0.5.13) but 0.5.2-3 is to be installed
  Depends: libqt3c102-mt (>=3:3.3.4) but 3:3.3.3-7ubuntu3 is to be installed
```

I tried using the KDEWallet to manage local passwords, but seems a bit of a PITA to use for this purpose. So hopefully these dependancy issues aren't too bad, though I have a bad feeling about the libc6 one.

Thanks!

Bob

---

### Post by Bob D. on 2005-06-23
Excuse me for a moment...

](*,)

There, now that I've gotten that out of the way.....

I see why there was no response to this post...it doesn't meet Requirement 0 for Backports (i.e. be in Breezy). It does help to READ the FAQ's BEFORE one posts.

OK, I'll try again in another thread. :)

Bob

---

