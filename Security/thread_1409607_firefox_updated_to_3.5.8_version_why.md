---
title: "firefox updated to 3.5.8 version why?"
date: 2010-02-17
forum: Security
---

### Post by dogdo on 2010-02-17
Hi

For some reason the update manager updated me to firefox '3.5.8' even though the most recent version is 3.6 [http://www.mozilla.com/en-US/firefox/3.6/releasenotes/](http://www.mozilla.com/en-US/firefox/3.6/releasenotes/) . Is this a update flaw?

---

### Post by rookcifer on 2010-02-17
> **dogdo said:**
> Hi

For some reason the update manager updated me to firefox '3.5.8' even though the most recent version is 3.6 [http://www.mozilla.com/en-US/firefox/3.6/releasenotes/](http://www.mozilla.com/en-US/firefox/3.6/releasenotes/) . Is this a update flaw?

I was just wondering the same thing.  However, 3.5.7 has already been out a while, so 3.5.8 would be the next logical step.  I can't find a changelog, though.

---

### Post by dogdo on 2010-02-17
The firefox website does not mention this version of firefox in the version history update section. I am suspicious. But since this update came from the repositories it should be safe yes?

---

### Post by ratcheer on 2010-02-17
It did this because 3.5 is the major version of FF supported by Karmic. 3.6 will be supported by Lucid. So, in my case, I was downgraded from 3.6 to 3.5.8 by the Software Manager. I will have to fix it. 

Tim

---

### Post by OrangeCrate on 2010-02-17
As a feature native to the release, you won't get 3.6 until Lucid (10.04) is released (unless you want to go get it yourself).

For the life of Karmic, you will receive point security updates, but no feature upgrades. That's the way that Ubuntu releases work.

So, Jaunty has 3.0, Karmic has 3.5, Lucid will have 3.6.

See here for additional info, on what's included with each release:

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

---

### Post by rookcifer on 2010-02-17
> **OrangeCrate said:**
> As a feature native to the release, you won't get 3.6 until Lucid (10.04) is released (unless you want to go get it yourself). For the life of Karmic, you will receive point security updates, but no feature upgrades. That's the way that Ubuntu releases work.

So, Jaunty has 3.0, Karmic has 3.5, Lucid will have 3.6 - See here for additional info:

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

Yes, but where can we find out info about what has changed in 3.5.8?  I don't see any details on the Mozilla website.

---

### Post by dogdo on 2010-02-17
> **rookcifer said:**
> Yes, but where can we find out info about what has changed in 3.5.8?  I don't see any details on the Mozilla website.

+1

Also what happens if a new feature update has security updates too-For example does firefox 3.6 include security patches not made available in 3.5?

---

### Post by OrangeCrate on 2010-02-17
> **rookcifer said:**
> Yes, but where can we find out info about what has changed in 3.5.8?  I don't see any details on the Mozilla website.

Firefox > Help > Release Notes

That's where the info will be listed, on all updates.

---

### Post by ratcheer on 2010-02-17
**Security Issues Fixed in Firefox 3.5.8**
MFSA 2010-05 XSS hazard using SVG document and binary Content-Type
MFSA 2010-04 XSS due to window.dialogArguments being readable cross-domain
MFSA 2010-03 Use-after-free crash in HTML parser
MFSA 2010-02 Web Worker Array Handling Heap Corruption Vulnerability
MFSA 2010-01 Crashes with evidence of memory corruption (rv:1.9.1.8/ 1.9.0.18)

Tim

---

