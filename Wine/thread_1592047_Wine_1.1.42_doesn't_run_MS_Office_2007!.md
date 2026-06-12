---
title: "Wine 1.1.42 doesn't run MS Office 2007!"
date: 2010-10-10
forum: Wine
---

### Post by jre6 on 2010-10-10
I have installed Wine 1.1.42 on Ubuntu 10.04.1, hoping to run Windows applications like MS Office 2007 on it as I have to handle a lot of MS Office files. Unfortunately, Wine fails to run the program and gives the following error when opening programs like Word, Excel and Powerpoint(see attachment).

How can I resolve this issue to make MS Office work on Ubuntu?

---

### Post by Soulcage on 2010-10-11
Are you trying to run it from your windows' partition? That is not allowed, it could destroy your windows' partition.
[http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2]("http://wiki.winehq.org/FAQ#head-497f1a295d53dd3444f211df2b13312c7767afa2")

Also 1.1.42 is really old you should use 1.2.1 or 1.3.4 [http://www.winehq.org/download/]("http://www.winehq.org/download/")

---

### Post by jre6 on 2010-10-11
Yes, I was trying to install this from my Windows partition.

I installed it on the Ubuntu partition and it worked.

But I cannot enter the product key in the installer.

Please help.

---

### Post by JustinR on 2010-10-11
> **jre6 said:**
> Yes, I was trying to install this from my Windows partition.

I installed it on the Ubuntu partition and it worked.

But I cannot enter the product key in the installer.

Please help.

Wine + Office 2007 don't completely cooperate together fully - there are problems.

You could look into SoftMaker Office, designed to be completely compatible with MS Documents.

---

### Post by jre6 on 2010-10-12
It took many attempts to install MS Office 2007 with Wine properly. But finally it worked and the I was able to insert the product key in the installer.

---

