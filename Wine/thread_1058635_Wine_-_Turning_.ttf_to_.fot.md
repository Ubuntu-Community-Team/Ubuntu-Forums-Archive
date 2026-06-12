---
title: "Wine - Turning .ttf to .fot"
date: 2009-02-03
forum: Wine
---

### Post by JohnWesleyMethodist on 2009-02-03
Hello!

I am running Wine 1.0.1. I posted this question in the General Help forum before realizing that there was a thread exclusive to Wine.

I am trying to install an old 95/98 program into Wine. It's called PC Study Bible 3. Well, actually the install went almost perfect and it works just fine, except one little problem:

Error in Creating C:\windows\SYSTEM\pcsbgrk.FOT From C:\windows\Fonts\pcsbgrk.ttf

Error in Adding Font Resource

Error in Creating C:\windows\SYSTEM\pcsbheb.FOT From C:\windows\Fonts\pcsbheb.ttf

Error in Adding Font Resource

I got those errors during installation, So basically the toolbar buttons do not have fonts, they are blank.

I have checked Google, but I don't see an exact fix for this, and all the references to this program are regarding newer versions of this app.

The .ttf files are in Wine in C:\windows\fonts, but the program needs to turn the .ttf files into .fot files and put them in C:\windows\system, and it is failing to do that.

I could cheat and grab the files off Windows and copy them into Wine, but I would like to gain independence from Windows, so I am looking for another method.

Anyone know what to do? In Windows apparently you just go in the control panel and select fonts, and somehow in there you register the font and the .fot file is added. How do I do it in Wine?

Thanks

---

### Post by jrusso2 on 2009-02-03
Cheat and copy it from Windows.  No one cares.

---

### Post by JohnWesleyMethodist on 2009-02-03
> **jrusso2 said:**
> Cheat and copy it from Windows.  No one cares.

 The issue is that I am pretending that I have now erased Windows off my hard-drive, and now what would I do to fix this without Windows access? This issue I am sure has broader implications than just my program.

 Update: Well, I have tried all sorts of stuff like putting the fonts in directories within Ubuntu. I noticed that the fonts in the Wine Registry all linked to locations in Ubuntu, not Windows locations. So I took the .ttf files from the installation disc and put them in the same locations of other fonts in Ubuntu and added them to the Wine Registry. That accomplished nothing.

---

### Post by JohnWesleyMethodist on 2009-02-03
> **jrusso2 said:**
> Cheat and copy it from Windows.  No one cares.

 I gave up and decided to copy those files from Windows in to Wine, and it still doesn't work.

---

