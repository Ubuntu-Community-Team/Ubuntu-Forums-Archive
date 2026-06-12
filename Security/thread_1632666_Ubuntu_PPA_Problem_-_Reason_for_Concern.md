---
title: "Ubuntu PPA Problem - Reason for Concern?"
date: 2010-11-28
forum: Security
---

### Post by linux-hack on 2010-11-28
Juste red this, and I find it rely interesting and hes right :
[http://jeffhoogland.blogspot.com/2010/11/ubuntu-ppa-problem-reason-for-concern.html](http://jeffhoogland.blogspot.com/2010/11/ubuntu-ppa-problem-reason-for-concern.html)
> With the release of Ubuntu 9.10 late last year Canonical introduced PPAs, which is short for Personal Package Archives. A PPA allows anyone that has signed the Ubuntu Code of Conduct to easily distribute software they have packaged to Ubuntu users. This revolutionary idea allows those who do not have the capability to establish their own repository to easily provide package updates to their users. Want the latest version of Openshot or PiTiVi? Then simply add a PPA to your system that packages up to date versions of these softwares and you will be set to go!

The problem with this system you ask? There is namely one issue: Canonical does not review any of the packages that are uploaded to PPAs. Because of this adding software from various PPAs wily nilly in reality is more dangerous than installing software on Windows. I say this because not only are you giving root access to the software upon installation, but also every time you run a system update from then after. Meaning even if a PPA provides trusted packages at first, this could change later on.

While it has not happened yet (as far as I am aware), I feel it is only a matter of time before some form of malicious code makes its way into a PPA that is used large scale. If you are comfortable with having software installed on your system from many different sources - that is your own choice (one of the many great things about FOSS). However, if you always need the latest up to date software maybe it is worth considering a rolling release distro such as LMDE or Chakra.

What is your take on this? Am I just blowing hot air and worrying for nothing or could having piles of PPAs on your system cause a potential risk down the line?

~Jeff Hoogland

---

### Post by movieman on 2010-11-28
Ultimately you should only use PPAs you trust: it's just like installing random software in Windows, if you can't trust the developer they can take over your entire system when you install their software.

---

### Post by linux-hack on 2010-11-28
> **movieman said:**
> Ultimately you should only use PPAs you trust: it's just like installing random software in Windows, if you can't trust the developer they can take over your entire system when you install their software.

And how can you know if you can trust them ?? Its not that easy ...

---

### Post by Enigmapond on 2010-11-28
> **linux-hack said:**
> And how can you know if you can trust them ?? Its not that easy ...

I think with the amount of people here in the forum you can pretty much see anything about any software. Trust ME.. :p if there was a problem you would see red flags all over this forum... one of the great things about the Linux community.

Cheers

---

### Post by movieman on 2010-11-28
If Ubuntu allowed you to limit a PPA to only updating its own software that would be an improvement: for example, xbmc puts most of its files under /usr/share/xbmc, and there are probably only a few other directories or files it needs to write to.

That way you could ensure that a PPA wouldn't overwrite important system files, or at least provide a warning if it tried to do so; obviously the software could still overwrite your personal files when you run it.

I guess the problem is that the PPA is allowed to run scripts as root when installing, so you'd need to wrap those scripts in an apparmor wrapper or something similar.

---

### Post by linux-hack on 2010-11-28
Yes I know that .. I juste want to know what the others think about this ... And for the community, I know there rely active and that the information is shared really quickly thats why I'm a member of it :D

---

### Post by linux-hack on 2010-11-28
> **movieman said:**
> 
I guess the problem is that the PPA is allowed to run scripts as root when installing, so you'd need to wrap those scripts in an apparmor wrapper or something similar.

Yes, your right ..

---

