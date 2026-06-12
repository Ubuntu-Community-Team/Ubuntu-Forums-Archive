---
title: "Ubuntu-Gnome: Firefox won't download adblock plus lists"
date: 2014-03-11
forum: Ubuntu Development Version
---

### Post by johnd03 on 2014-03-11
Hi.


It's very weird, that Firefox cannot download the lists for the adblock plus addon. I cant even access just the link to the list. 
[https://easylist-downloads.adblockplus.org/exceptionrules.txt](https://easylist-downloads.adblockplus.org/exceptionrules.txt)

Tried it with my host and with a fresh installed version of ubuntu gnome. Result is exactly the same. "Server not found".

I asked in the #ubuntu+1 channel if anyone could try that link. One with Kubuntu 14.04 tested it and it worked. 
It's also working with xubuntu/ubuntu 12.04 or other distributions like debian or centos. 

So I'm wondering how that could be possible, that it works with kubuntu 14.04 but not with ubuntu gnome?

Please be so kind and test it with ubuntu gnome and let me know. Something must be different not just the DE. Something must prevent firefox from downloading and accessing that page... but what? :/


regards

jd

---

### Post by QDR06VV9 on 2014-03-11
Works Here with Gnome-Shell.
Have you tried a new profile?
Terminal "firefox -p"

---

### Post by echotech2 on 2014-03-12
Did you see this (easyList Forum)?  [http://forums.lanik.us/viewtopic.php?f=23&t=15902](http://forums.lanik.us/viewtopic.php?f=23&t=15902)

---

### Post by QDR06VV9 on 2014-03-12
Very Strange? I have no issues.

---

### Post by conualfy on 2014-03-30
I am having the same problem after I reinstalled my system a few days ago. Everything else seems to work, but not the adblockplus lists and not the Firefox sync. I guess they are related. It works fine in Chromium, so it is not a network problem. I have reported this bug on Mozilla Bugzilla - [https://bugzilla.mozilla.org/show_bug.cgi?id=988819](https://bugzilla.mozilla.org/show_bug.cgi?id=988819), please comment there too, so they take it serios. Until now I look like the only crazy guy with this problem. I use Ubuntu 13.10, all updates since installation, amd64 version.

---

### Post by forcecore on 2014-03-31
I had this problem weeks ago and fanboy list worked fine as a easylist replacement.

---

### Post by Smask on 2014-03-31
There are 4 extensions installed made by Canonical. Sometimes they may interfere with some function/extension. Me, I couldn't add search extensions from Mycroftproject until I disabled the Ubuntu-provided extension. Which one was the culprit? I don't know as I disabled all 4 in one go.


Have you tried disable those? Begins with "Ubuntu" and "Unity". You can't remove them from within Firefox, only disable.

---

