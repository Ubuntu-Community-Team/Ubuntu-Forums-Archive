---
title: "[SOLVED] encryption software for linux and windows?"
date: 2008-11-12
forum: The Cafe
---

### Post by smoker on 2008-11-12
hi, i have a need for some good encryption software (opensource, or at least free!) that can be installed on both linux and windows computers. for basically transferring sensitive data between systems using usb flash drives. must have an easy gui for the windows users!

anyone got any recommendations?

---

### Post by ubuntu27 on 2008-11-12
There is nothing better than [TrueCrypt]("http://www.truecrypt.org/"), an Free open-source disk encryption software for Windows Vista/XP, Mac OS X, and Linux

[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by bobbob94 on 2008-11-12
Truecrypt sounds like it might fit the bill for what you need . I use it myself and like it...

---

### Post by binbash on 2008-11-12
+1 truecrypt.It is awesome

---

### Post by smoker on 2008-11-12
thanks all, looks like i'll try out 'truecrypt',

cheers :-)

---

### Post by tom66 on 2008-11-12
I used truecrypt, worked like a charm, but I don't use it now.

---

### Post by Dr Small on 2008-11-12
+5 for truecrypt.

---

### Post by handy on 2008-11-13
I was looking into encryption the other day, I didn't come across Truecrypt.

Thanks for the heads up it looks like just what I was after, & it is available in the Arch Extra repo' & 64bit too. :-)

---

### Post by poebae on 2008-11-13
I don't mean to hijack this thread, but I have a simple question.

I don't know much about encryption, but the question that struck me when I read this thread was "can open source encryption be truly secure?" How does it work exactly, and how is it kept secure despite people knowing its inner workings?

---

### Post by OutOfReach on 2008-11-13
> **handy said:**
> it is available in the Arch Extra repo' & 64bit too. :-)

Thank YOU for the heads up, I was about to manually download it. :)

---

### Post by samjh on 2008-11-13
> **poebae said:**
> I don't mean to hijack this thread, but I have a simple question.

I don't know much about encryption, but the question that struck me when I read this thread was "can open source encryption be truly secure?" How does it work exactly, and how is it kept secure despite people knowing its inner workings?

The strength of encryption is dependant on its mathematical basis and the quality of the "key" used, not the implementation code.

If the code is sloppy, it can create vulnerabilities.  But any good programmer will be able to prevent that.  It's the math and the user's key that really matter.

As for the math, every high-profile encryption method has its algorithm published for academic and industry scrutiny.  Close scrutiny by academia and industry is essential in order to detect weaknesses.

So in conclusion, yes, open source encryption can be safe, as long as the code which implements the encryption algorithm is properly written, and the end-user uses appropriate keys.

---

### Post by poebae on 2008-11-13
> **samjh said:**
> The strength of encryption is dependant on its mathematical basis and the quality of the "key" used, not the implementation code.

*SNIP*
Thanks for the prompt answer; clears things up for me :)

---

### Post by dirtrider1 on 2011-09-30
> **poebae said:**
> I don't mean to hijack this thread, but I have a simple question.

I don't know much about encryption, but the question that struck me when I read this thread was "can open source encryption be truly secure?" How does it work exactly, and how is it kept secure despite people knowing its inner workings?

One of the big factors of how secure an encryption algorithm or even the encryption software is how well it has been tested. Open source software is actually generally more secure because the source code is available. The code usually get's scrutinized much more thoroughly and by many more people. "Given enough eyeballs, all bugs are shallow". I actually only trust encryption software that is free/open source, that way it is verifiable. It is well known certain proprietary vendor's work very closely with certain government agencies and it's very possible there could be some kind of backdoor or vulnerability not publicly known.

---

### Post by szymon_g on 2011-09-30
> **dirtrider1 said:**
> The code usually get's scrutinized much more thoroughly and by many more people. "Given enough eyeballs, all bugs are shallow". I actually only trust encryption software that is free/open source, that way it is verifiable.

hm... it is as safe as Debian's (and Ubuntu's) openssl package ( [http://digitaloffense.net/tools/debian-openssl/](http://digitaloffense.net/tools/debian-openssl/) ) ;)?


> **dirtrider1 said:**
> It is well known certain proprietary vendor's work very closely with certain government agencies and it's very possible there could be some kind of backdoor or vulnerability not publicly known.

FUD must go on...

---

### Post by alphacrucis2 on 2011-09-30
One thing to note about truecrypt is the licence. From Wikipedia:

[QUOTE="Wikipedia"]The TrueCrypt License has not been officially approved by the Open Source Initiative and is not considered "free" by several major Linux distributions (Arch Linux,[35] Debian,[36] Ubuntu,[37] Fedora,[38] openSUSE,[39] Gentoo[40]), mainly because of distribution and copyright-liability reasons.[41]

TrueCrypt 6.3a (released Nov 2009) comes under TrueCrypt License Version 2.8 which was changed in some places from the 2.5 license, but TrueCrypt is still not included in any of the major Linux distributions.[/QUOTE]

This is why it isn't the ubuntu repos I guess.

---

### Post by szymon_g on 2011-09-30
> **alphacrucis2 said:**
> This is why it isn't the ubuntu repos I guess.

on Fedora it's called "Realcrypt". maybe it is it's name in ubuntu as well?

---

### Post by alphacrucis2 on 2011-09-30
> **szymon_g said:**
> on Fedora it's called "Realcrypt". maybe it is it's name in ubuntu as well?

Interesting. It doesn't show up in synaptic under either realcrypt or truecrypt. I found a couple of posts regarding the renaming and inclusion in rpmfusion for fedora and it sounds like Mandriva did something similar.

[http://www.fedoraforum.org/forum/showthread.php?t=193960](http://www.fedoraforum.org/forum/showthread.php?t=193960)

---

