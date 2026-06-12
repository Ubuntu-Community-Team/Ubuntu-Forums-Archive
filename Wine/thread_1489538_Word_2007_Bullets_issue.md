---
title: "Word 2007 Bullets issue"
date: 2010-05-21
forum: Wine
---

### Post by megamaced on 2010-05-21
Hi,

I have successfully installed Office 2007 using this guide: [http://www.wine-reviews.net/wine-reviews/microsoft/office-2007-in-ubuntu-910-with-wine-1132.html](http://www.wine-reviews.net/wine-reviews/microsoft/office-2007-in-ubuntu-910-with-wine-1132.html)

I am running Lucid and the PPA branch of Wine, now at 1.1.44-0ubuntu1~lucidppa1

Everything appeared to be working fine, then I noticed that in one particular document I am using tick marks for my bullet points but they are not being displayed correctly. Then I noticed that a lot of the bullet point styles are not displayed properly. Usually the bullets are replaced by a square or garbage.

I have copied over the symbol.ttf font from my Windows 7 machine but it made no difference

Can anyone help?

Cheers

---

### Post by hemimaniac on 2010-05-21
sudo aptitude install abiword

Sorted

:popcorn:

---

### Post by Merk42 on 2010-05-23
> **hemimaniac said:**
> sudo aptitude install abiword

Sorted

:popcorn:

:roll:


Anyway, megamaced, do you have that problem if you use a native linux application? Just trying to figure out if it's a problem with the font you're using or WINE, or what.  You may be using some font WINE doesn't know, did you try installing ttf-mscorefonts-installer or even just changing the font in your documents?

---

### Post by megamaced on 2010-05-24
I did run, or at least I thought I had run, the MS fonts installer in Wine using Winetricks. Either way, I copied over Webding.ttf, wingding.ttf, wingdng2.ttf and wingdng3.ttf from my Windows 7 with Office 2007 installed, and now my tick bullets display OK.

W00t!

---

### Post by abelandlinux on 2011-07-08
Where did you copy those files to?

---

### Post by Dlambert on 2011-07-09
I think LibreOffice is better than Abiword in my opinion

---

### Post by joonpy on 2012-10-14
> **megamaced said:**
> I copied over Webding.ttf, wingding.ttf, wingdng2.ttf and wingdng3.ttf from my Windows 7 with Office 2007 installed, and now my tick bullets display OK.


Thanks a lot for this information.

---

### Post by aabed91 on 2012-10-14
when i install ubuntu for first time i can't believe OS without MS Office

i tried libre office but it's not what i need

but finally i found open office and it very nice in my opinion

---

