---
title: "Themida - Internal Exception Occured"
date: 2010-09-15
forum: Wine
---

### Post by rubencouto on 2010-09-15
Hello!

I have Wine 1.1.42 installed under Ubuntu 10.04 LTS. I installed MetaTrader 4 (from [www.IBFX.com](www.IBFX.com)) and it seemed to get properly installed.

Now, everytime I try to run MetaTrader, I get a Themida error message window, saying that an internal exception has occured. The application MetaTrader does not load.

I have no idea what to do. Is there something I must configure on Wine? Is Themida a virus camouflage software? If so, how do I remove it?

Any ideas!
:)

---

### Post by lkjoel on 2010-09-15
> **rubencouto said:**
> Hello!

I have Wine 1.1.42 installed under Ubuntu 10.04 LTS. I installed MetaTrader 4 (from [www.IBFX.com](www.IBFX.com)) and it seemed to get properly installed.

Now, everytime I try to run MetaTrader, I get a Themida error message window, saying that an internal exception has occured. The application MetaTrader does not load.

I have no idea what to do. Is there something I must configure on Wine? Is Themida a virus camouflage software? If so, how do I remove it?

Any ideas!
:)
Try getting Wine 1.3.2 ([http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb"))

---

### Post by williamlive on 2010-09-15
i got same prob with u ruben, 1st it said mfc42.dll is missing, after i get the file ini igot error themida

here i attach my SC

(i'm using wine 1.3 now and wine 1,2 have same prob too)

---

### Post by lkjoel on 2010-09-16
> **williamlive said:**
> i got same prob with u ruben, 1st it said mfc42.dll is missing, after i get the file ini igot error themida

here i attach my SC

(i'm using wine 1.3 now and wine 1,2 have same prob too)
WINE does not support all applications.
Check out [http://appdb.winehq.org]("http://appdb.winehq.org")

---

### Post by williamlive on 2010-09-16
> **lkjoel said:**
> WINE does not support all applications.
Check out [http://appdb.winehq.org](http://appdb.winehq.org)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2893](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2893)

cek it out

**Additional Comments**
install visual c runtimes with winetricks vcrun6.
i don't understand this additional comments

---

### Post by rubencouto on 2010-09-17
I thank for all the inputs!
 
Is Themida in any way connected or related to Wine?

---

### Post by iNerdSure on 2010-10-30
> **rubencouto said:**
> I thank for all the inputs!
 
Is Themida in any way connected or related to Wine?

I run MetaTrader 4 (from FXDD) on Wine-1.2. (on Ubuntu 10.04)  You can download the missing mfc42.dll from [www.dlldump.com]("www.dlldump.com").

You can also improve the appearance of MT4 by running "winetricks" with "allfonts".

---

