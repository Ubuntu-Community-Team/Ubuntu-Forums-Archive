---
title: "e-Sword 10.x Issues with Wine"
date: 2013-03-27
forum: Ubuntu Christian Edition
---

### Post by jonathonblake on 2013-03-27
[http://ubuntuforums.org/showthread.php?t=404042&page=21&p=12576234#post12576234](http://ubuntuforums.org/showthread.php?t=404042&page=21&p=12576234#post12576234) contains a current (20130327) script for installing e-Sword 10.1.

AFAIK, the following are known issues with e-Sword 10.1 under WINE, that have no known solution:
[LIST]
[*]Audio Sermon does not work;
[*]Highlighting, and other markup does not stay;
[*]Normal search is not functional;
[/LIST]

###

Starting a new thread, becuase the old thread contains a lot of information that works for e-Sword 7.x, 8.x, and 9.x, that is not useful for e-Sword 10.1.x, and higher.

jonathon

---

### Post by revdjenk on 2013-05-11
> **jonathonblake said:**
> [http://ubuntuforums.org/showthread.php?t=404042&page=21&p=12576234#post12576234](http://ubuntuforums.org/showthread.php?t=404042&page=21&p=12576234#post12576234) contains a current (20130327) script for installing e-Sword 10.1.

AFAIK, the following are known issues with e-Sword 10.1 under WINE, that have no known solution:
[LIST]
[*]Audio Sermon does not work;
[*]Highlighting, and other markup does not stay;
[*]Normal search is not functional;
[/LIST]

###

Starting a new thread, becuase the old thread contains a lot of information that works for e-Sword 7.x, 8.x, and 9.x, that is not useful for e-Sword 10.1.x, and higher.

jonathon


Thanks for the re-direct Jonathon! Maybe this will help us with the latest, 10.1 and later versions of e-sword!

I found that search does work with david_kt post #823 with his latest e-sword installer found there. This is soooo much easier than a manual install!

However, I use Hebrew and Greek Bibles, and most do not render the fonts correctly after this install, just gibberish characters. I have run wintricks to install all the suggested dll's and winecfg to add the rich20 and oleaut32 to the libraries.  Still not corrected.  Anyone with ideas?

God Bless, Doug

---

### Post by jonathonblake on 2013-08-05
> **revdjenk said:**
> 
However, I use Hebrew and Greek Bibles, and most do not render the fonts correctly after this install, just gibberish characters. I have run wintricks to install all the suggested dll's and winecfg to add the rich20 and oleaut32 to the libraries.  Still not corrected.  Anyone with ideas?

If you see squares, then you need to install a different font.
If a Greek, Hebrew, Aramaic, or Coptic text is showing characters from the Latin writing system, then the resource was incorrectly constructed.  You'll either need to reconstruct it correctly, or download one that was correctly constructed.

jonathon

---

### Post by david_kt on 2013-08-06
> **revdjenk said:**
> However, I use Hebrew and Greek Bibles, and most do not render the fonts correctly after this install, just gibberish characters. I have run wintricks to install all the suggested dll's and winecfg to add the rich20 and oleaut32 to the libraries.  Still not corrected.  Anyone with ideas?

God Bless, Doug

You have to add :
env WINEPREFIX=~/.wine_Esword
for all the tweaks to get it working. Otherwise, the tweak would be install on default wine, which does not affect e-Sword.

DK

---

