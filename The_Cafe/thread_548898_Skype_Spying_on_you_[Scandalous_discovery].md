---
title: "Skype Spying on you? [Scandalous discovery]"
date: 2007-09-11
forum: The Cafe
---

### Post by ubuntu27 on 2007-09-11
GNU/Linux Users of the P2P telephonic service Skype discovered that that software reads surreptitiously files contained in /etc/passwd and the profiles and configuration of the plugins installed for Firefox.

This was revealed by using AppArmor and confirmed by users of Skype version 1.4.0.94 and 1.4.0.99. 
Surely this event shows the how valuable AppArmor is fir revealing the behaviour of any source closed application.

The first discovery was originally made with Skype 1.4.0.99 in Ubuntu Gutsy Gibbon Tribe-4.

    * [Complete Article in Slashdot]("http://yro.slashdot.org/article.pl?sid=07/08/26/1312256&from=rss")

I found it originally at [VivaLinux]("http://www.vivalinux.com.ar/soft/skype-descubierto-con-apparmor.html") (SPANISH SITE)

It has a link on [Skype on Linux]("http://forum.skype.com/index.php?showtopic=95261") (ENGLISH)

---

### Post by DownTown22 on 2007-09-11
I'm gonna say.....no.

---

### Post by Andrewie on 2007-09-11
this was on slashdot awhile ago. There are a lot of reasons to read etc/passwd. And it checked the firefox folder to see if you have the plugin installed.

---

### Post by nonewmsgs on 2007-09-11
i read all 5 pages (even included the developers to talk) and it seems like it's not that big of a deal.  i was rather impressed by the devs about they really did seem to try to explain it despite some rather flaming trolls.

---

### Post by mikewhatever on 2007-09-11
> **ubuntu27 said:**
> GNU/Linux Users of the P2P telephonic service Skype discovered that that software reads surreptitiously files contained in /etc/passwd and the profiles and configuration of the plugins installed for Firefox.


As the discussion at [http://forum.skype.com/index.php?showtopic=95261](http://forum.skype.com/index.php?showtopic=95261) reveals, a lot of other programs read /etc/passwd. Don't blow it out of proportions.
As a side note, hope skype 1.4 will get out of beta by the end of the year, or next year, more likely.

---

### Post by ubuntu27 on 2007-09-11
> **Andrewie said:**
> this was on slashdot awhile ago. 

Uh! I just saw that this slashdot article is ONE (August) month old! How did I miss that?

---

### Post by jsbach on 2007-09-12
I'd be interested to hear people's opinions on Skype for Linux accessing people's private firefox directories. strace -e open -f skype 2> SKYPE, for me shows 179 references to my private mozilla files being read, including passwords, usernames, bank acount details etc.

The point is surely that skype shouldn't be accessing that data at all. in fact, in my country, it is illegal under sections 1 & 2 of Computer Misuse Act 1990 - 

[http://www.opsi.gov.uk/acts/acts1990/Ukpga_19900018_en_1.htm](http://www.opsi.gov.uk/acts/acts1990/Ukpga_19900018_en_1.htm)

Skype's stated policy :

[http://www.skype.com/download/adwarefree/](http://www.skype.com/download/adwarefree/)

The people here who have stated that this is a non-issue are either misinformed or misinformers or both.

---

### Post by ubuntu27 on 2007-09-12
From what I been reading, in "modern" GNU/Linux the directory /etc/passwd doesn't contain password at all. Can someone confirm this?

I just opened in my comp, and it contains usernames (user accounts), some random numbers, and a path or directory to something.

---

### Post by jsbach on 2007-09-12
True ubuntu27, but I don't care about /etc/passwd.

I care about my *private* firefox files, including all extensions, plugins etc. These files contain private and sensitive personal data, which I most certainly have NOT given Skype permission to access.

That is the real scandal. And it is an issue that will land them in court facing criminal charges.

The whole issue has been side-tracked with spurious /etc/passwd verbiage, in my view at least.

---

### Post by Nekiruhs on 2007-09-12
> **jsbach said:**
> I'd be interested to hear people's opinions on Skype for Linux accessing people's private firefox directories. strace -e open -f skype 2> SKYPE, for me shows 179 references to my private mozilla files being read, including passwords, usernames, bank acount details etc.

The point is surely that skype shouldn't be accessing that data at all. in fact, in my country, it is illegal under sections 1 & 2 of Computer Misuse Act 1990 - 

[http://www.opsi.gov.uk/acts/acts1990/Ukpga_19900018_en_1.htm](http://www.opsi.gov.uk/acts/acts1990/Ukpga_19900018_en_1.htm)

Skype's stated policy :

[http://www.skype.com/download/adwarefree/](http://www.skype.com/download/adwarefree/)

The people here who have stated that this is a non-issue are either misinformed or misinformers or both.
I saw your post in the thread. The devs have told you what its for. The burden of proof here is on you.

---

### Post by jsbach on 2007-09-12
Nekirus, what POSSIBLE excuse can there be for Skype accessing PRIVATE data from another application ?

As I've stated before, I have not given Skype permission to do that, and they are therefore breaking the law.

It couldn't be more simple.

---

### Post by twisted_steel on 2007-09-12
> **ubuntu27 said:**
> From what I been reading, in "modern" GNU/Linux the directory /etc/passwd doesn't contain password at all. Can someone confirm this?

I just opened in my comp, and it contains usernames (user accounts), some random numbers, and a path or directory to something.

A hashed version for the users is in /etc/shadow.  This gives a quick breakdown: [http://en.wikipedia.org/wiki/Shadow_password](http://en.wikipedia.org/wiki/Shadow_password)

---

### Post by Nekiruhs on 2007-09-12
> **jsbach said:**
> Nekirus, what POSSIBLE excuse can there be for Skype accessing PRIVATE data from another application ?

As I've stated before, I have not given Skype permission to do that, and they are therefore breaking the law.

It couldn't be more simple.
I fail to see how listing the files and finding prefs.js is the same as opening and searching through each file and extracting your data.

---

### Post by jsbach on 2007-09-12
Nekirus, you are being a little disingenuous.

Those files were OPENED for reading and then read. To suggest that it was just a listing of those files is nonsense.

I think we know where YOU stand on this matter.

---

### Post by revertex on 2007-10-21
it's a little deeper, it look for other files, like opera thunderbird and kde.

```
open("/home/revertex/.mozilla", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 32
open("/home/revertex/.mozilla/firefox", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 31
open("/home/revertex/.mozilla/firefox/XXXXXX.default", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 33
open("/home/revertex/.mozilla/firefox/XXXXXX.default/chrome", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 34
open("/home/revertex/.mozilla/firefox/XXXXXX.default/extensions", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 34
open("/home/revertex/.mozilla/firefox/XXXXXX.default/extensions/{XXXXX-XXXX-XXXX-XXXX-XXXX}", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 35
open("/home/revertex/.mozilla/firefox/XXXXXX.default/extensions/staged-xpis", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 35
open("/home/revertex/.mozilla/firefox/XXXXXX.default/extensions/staged-xpis/{XXXX-XXXX-XXXX-XXXX-XXXX}", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 36
open("/home/revertex/.mozilla/firefox/XXXXXX.default/bookmarkbackups", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 34
open("/home/revertex/.mozilla/sunbird", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 31
open("/home/revertex/.mozilla/sunbird/XXXXXX.default", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 33
open("/home/revertex/.mozilla/sunbird/XXXXXX.default/extensions", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 34
open("/home/revertex/.mozilla/iceowl", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 31
open("/home/revertex/.mozilla/iceowl/XXXXXX.default", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 33
open("/home/revertex/.mozilla/iceowl/XXXXXX.default/extensions", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 34
open("/home/revertex/.mozilla/plugins", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 31
open("/home/revertex/.mozilla/firefox/XXXXXX.default/prefs.js", O_RDONLY) = 31
open("/home/revertex/.kde/share/config/kioslaverc", O_RDONLY) = 31
open("/home/revertex/.opera/opera6.ini", O_RDONLY) = -1 ENOENT (No such file or directory)
```

---

