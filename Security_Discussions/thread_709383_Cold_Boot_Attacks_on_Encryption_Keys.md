---
title: "Cold Boot Attacks on Encryption Keys"
date: 2008-02-27
forum: Security Discussions
---

### Post by suibhne on 2008-02-27
This research is worrying - disk encryption  defeated by simple methods. 

The research illustrates methods to defeat 

1. BitLocker (windows)

2. FileVault ( MacOS X)

_[COLOR="Red"]**[U]3. dm-crypt (GNU/Linux)_**[/COLOR][/U]

There's a good presentation and video at _[COLOR="Blue"][http://citp.princeton.edu/memory/](http://citp.princeton.edu/memory/)[/COLOR]_


commentary available on [COLOR="Blue"]_[http://www.freedom-to-tinker.com/?p=1257](http://www.freedom-to-tinker.com/?p=1257)_[/COLOR]

and if you are interested further:

[COLOR="Blue"]_[http://www.news.com/2300-1029_3-6230933-1.html](http://www.news.com/2300-1029_3-6230933-1.html)_[/COLOR]
[U][COLOR="Blue"]
[http://www.news.com/8301-13578_3-9876060-38.html](http://www.news.com/8301-13578_3-9876060-38.html)[/COLOR][/U]

---

### Post by tubezninja on 2008-02-27
Quite an interesting read.  I have to say I've not used the full-volume encryption tools myself, favoring instead to use TrueCrypt, or the built-in encrypted dmg tool in Mac OS X to encrypt and save sensitive personnel data and HR docs.  Wonder if the same attack methods can be applied for these methods?

EDIT:  The looks like the CNet article claims the answer to my question is no.

---

### Post by euler_fan on 2008-02-27
> [Translation: If you use an encrypted file-system and want privacy and security when you're not using your computer, you need to shut down your computer and wait a few minutes for the RAM contents to vanish. Another option for sensitive files is to use an encrypted volume like a PGP disk and unmount it as soon as you're done.]("http://www.news.com/8301-13578_3-9876060-38.html")

I think the critical part here is "unmount it as soon as you're done" and--implicitly--wait by your machine for a few minutes. Keys stored in RAM are vulnerable, not just ones for full disk encryption techniques.

This is more evidence an attacker with physical access to your machine can do whatever they want.

---

