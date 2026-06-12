---
title: "Photoshop CS4 and Wine"
date: 2010-03-07
forum: Wine
---

### Post by connorthecreator on 2010-03-07
Hi, I  recently installed Ubuntu 9.10 on one of my computers so I decided to join the forums In case I had a problem (like this one), so let me get to the point.

I'm trying to install Photoshop CS4, I can get as far as the screen that you have to choose between trial or key, my only problem is, all thats showing up is the background and next and quit buttons.

any help at all will be loved ^^

---

### Post by puzzler995 on 2010-03-07
Welcome to the Ubuntu Community!!!:KS

Unfortunately CS4 doesn't run under Wine. This link is a site that is a good resource to have if you are planning to run things off Wine. It will save you a LOT of trouble.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14318)

---

### Post by connorthecreator on 2010-03-07
hmm... well, I guess thats not gonna happen... does anyone have any Idea if I can use Pain tool sai under wine?

---

### Post by puzzler995 on 2010-03-07
what version do you have?

---

### Post by connorthecreator on 2010-03-07
version Ver.1.1.0 English translation

---

### Post by puzzler995 on 2010-03-07
you MIGHT have some good luck with that.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15221&iTestingId=35952](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15221&iTestingId=35952)

If not have you tried GIMP yet?

---

### Post by connorthecreator on 2010-03-07
I tried Gimp once, It scared me... probably because I've been using Photoshop for.. forever...

---

### Post by connorthecreator on 2010-03-07
and its a no go, guess I'll give and just use Gimp, or maybe I'll run a Virtual machine, probably both XD

---

### Post by mtdesign on 2010-03-10
I have gotten Photoshop CS2 to work under WINE with no problems so if people cant get CS4 to work try using CS2 instead if you really want PS

---

### Post by puzzler995 on 2010-03-10
Seriously??? :D I've got copies of both Dreamweaver MX 2004 and CS2. I assumed CS2 wouldn't work so I didn't try it. SO happy it might work

---

### Post by mtdesign on 2010-03-11
> **puzzler995 said:**
> Seriously??? :D I've got copies of both Dreamweaver MX 2004 and CS2. I assumed CS2 wouldn't work so I didn't try it. SO happy it might work

Yeah..you can also use Wine-Doors (google it) and download PS2 right from there, I dunno if it might cause less problems during install or not.

more information provided by the link below

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2631")

---

### Post by temenex on 2010-03-12
I have Wine 1.0.1 and Photoshop CS. Work well. :D

---

### Post by linux.is.skynet on 2010-04-10
Yeah, CS4 works in the current version of WINE. All you have to do is downgrade WINE to 1.1.17 and get winetricks. Paste this into your terminal to get winetricks :

 wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) 

Then paste :  

sh winetricks msxml6 gdiplus gecko vcrun2005 ie6

Then cd to the directory where setup.exe is on the disk and paste: 

LANG=C wine Setup.exe 

Then it should install and run. The only problem I've had is the tool boxes turning grey while I drag them across the screen, but they reappear when I drop them. It does it if I have 3D effects enabled or not, in KDE and Gnome. BUT it doesn't do it on systems with ATI cards, only Nvidia. I've tried older, trusted drivers and the newest. I think it just hates me. :o) Hope this helps.

---

### Post by linux.is.skynet on 2010-04-10
I forgot.... you can reinstall 1.1.42 or whichever WINE version you want AFTER it is installed.

---

