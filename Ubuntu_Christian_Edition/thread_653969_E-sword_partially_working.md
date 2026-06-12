---
title: "E-sword partially working"
date: 2007-12-30
forum: Ubuntu Christian Edition
---

### Post by aggiedvm on 2007-12-30
I started with Fiesty trying to install E-sword.  When I get it installed it would not display tips or the Bible modules.  KJV+ was listed but not text.  I tried manual install as described but not avail.  After installing Gusty and Wine updates I have been able to get KJV+ to display by adding the riched20, riched32 and oleau32 to the libraries in the config file.  I also added E-sword to the applications list in config and set it to Windows 98.  this is also after I completely deleted Wine and re-installed from Wine website.  After installing from here the config file is graphical.

I still cannot install the modules.  It starts and a window comes up and says Wizard is starting please wait.  I have to re-boot to get rid of the window.  Any ideas on how to get modules to load?  I would really like to have access to download NIV but I cannot get any of the free modules to load.  Also I lost the add modules program from the accessories list when I deleted Wine and re-installed.  Is there anyway to get that back?

Thanks,

Ken

---

### Post by jgt157 on 2007-12-31
I was able to get e-Sword installed and running, but I don't see any text in the tips window, the bible window, the commentary window or the window for the concordances/dictionaries.  I set the program to run in windows98, windows XP and Use Global Settings.  Your also supposed to set two of the dll's to run in native mode, but I'm unable to using winecfg.  When I select the dll, the Add button is grayed out. I'm assuming that's what is causing the problem with no text.  Any ideas would be helpful.

Jim T

---

### Post by aggiedvm on 2007-12-31
Jim,
My add buttons in library became active as soon as I started typing in the add window.  I added all three dll's to the library directory.  Riched20, riched32 and oleaut32.  At first I also unchecked the "Allow windows manager to control window."  However, it seems to be running with that checked now and it is easier to move between windows when the box is checked. 

I have still been unable to add any modules.  A box comes up asking me to wait while it loads but then nothing happens.  Let me know if any of this helps.  

Ken

---

### Post by jgt157 on 2008-01-01
Ken,

Yup, that fixed it for me.  Thanks!  I'll try to install the modules and let you know how it goes.

Jim

---

### Post by steveneddy on 2008-01-01
Try gnome-sword.

---

### Post by jgt157 on 2008-01-01
Tried installing a couple of modules and ran into the same problem, the wizard freezes as soon as it starts.  

Jim T

---

### Post by jgt157 on 2008-01-01
I went around the installation problem for the commentaries, dictionaries and bibles.  I have them installed on my Vista laptop so I just ftp'd the files over to my Kubuntu Gutsy system and put them in my e-Sword directory and they came right up when I started e-Sword.  My problem is solved.

Shalom,

Jim T

---

### Post by aggiedvm on 2008-01-02
Jim,

I loaded Crossover and installed it from there and worked fine first try.  I think the program is only about 40 dollars.

I got a reply from Frank from the Wine site and it worked on his computer when he added Riched20 and Riched32.  He did not say specifically if he was able to download modules though.

Have a great new year.

Ken

---

### Post by ElEdwards on 2008-01-10
> **jgt157 said:**
> I went around the installation problem for the commentaries, dictionaries and bibles.  I have them installed on my Vista laptop so I just ftp'd the files over to my Kubuntu Gutsy system and put them in my e-Sword directory and they came right up when I started e-Sword.  My problem is solved.

Shalom,

Jim T

Since I dual-boot with XP, I followed Jim's example.  I installed e-Sword on Linux and then on XP, then I installed the modules I wanted on XP, then I copied the **.bbl**, **.cmt** and **.dct** files to the Linux installation and everything was there... all the Bible versions, the Commentaries and Dictionaries. :)

El

---

### Post by dosh on 2008-01-19
Ken NIV is copyrighted so it is very unlikely you would find a free copy to download,

---

### Post by david_kt on 2008-01-28
> **aggiedvm said:**
> Jim,

I loaded Crossover and installed it from there and worked fine first try.  I think the program is only about 40 dollars.

I got a reply from Frank from the Wine site and it worked on his computer when he added Riched20 and Riched32.  He did not say specifically if he was able to download modules though.

Have a great new year.

Ken

It is good to buy crossover, because crossover is the company behind wine. Crossover could help you run a lot of think easy. But if you just want to run e-sword and not willing to buy crossover, you could try below how to:

[http://ubuntuforums.org/showthread.php?t=404042]("http://ubuntuforums.org/showthread.php?t=404042")

It could install latest version of esword (794) and using latest wine (0.9.54). It could install e-sword and even it's modules without any problem. Furthermore, you could install it on any distro you want, as long as it could run wine.

DK

---

### Post by aggiedvm on 2008-02-04
Thanks to all.  I have purchased Crossover - wanted to use for some of the other software as I try to make transition to Linux.  

To previous post I knew NIV is copyrighted but did not want to pay for it until I had a program in Linux that would load the NIV version.

Thanks again,

Ken

---

