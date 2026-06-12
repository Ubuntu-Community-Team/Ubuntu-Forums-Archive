---
title: "Desktop Trashcan for Lubuntu"
date: 2012-02-07
forum: Tutorials
---

### Post by ronniew on 2012-02-07
I've read that a trashcan for lxde/pcmanfm is a bit difficult to impliment. Thankfully pcmanfm eventually supported trash however it still does not provide a desktop icon for the trashcan..

To be honest it doesn't bother me. But some that I setup with Lubuntu miss the trashcan so I usually place a desktop icon (trashcan) on the desktop that opens and points to the trash.

It doesn't support drag & drop or right click empty trash but it gives users a reminder to check their trashcan and empty it if necessary from pcmanfm.

Pretty easy. Right click on the desktop and create a new file. Name it Trash.desktop   

Then right click on it and open the file with leafpad and copy and paste this in below and save.

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Name=Check Trash
Comment=Browser
Exec=pcmanfm trash:///
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=gnome-stock-trash.svg
Categories=Application;Desktop;Filemanager
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;
StartupWMClass=Pcmanfm
StartupNotify=true

```


I usually name it Check Trash or View Trash. You can name it whatever you want. I try to stick with those names to remind the user to open the trash then empty.

Here is a screenshot....

[http://picpaste.com/trash-1Qe0teqC.png]("http://picpaste.com/trash-1Qe0teqC.png")


Hope someone finds it useful.

---

### Post by SteveDee on 2012-02-08
> **ronniew said:**
> ...Hope someone finds it useful.

Good tip ronniew. Some users do feel happier with a Trash can.

Like you, I don't use one. But I do put a folder in my /home/steve/Desktop folder called "stuff". As stuff builds up on my desktop (which I hate) I either <shift><del> or (if I think I might need it a while longer) I drag it into my stuff folder for removal at a later day (...my garage is full of junk as well!).

---

### Post by AleveSicofante on 2012-02-14
> **ronniew said:**
> It doesn't support drag & drop or right click empty trash
This is major drawback for LXDE. I was about to put it in place of a Windows XP install, but it won't be accepted by its user without a proper trashcan or home folder in desktop.

:-(

---

### Post by ronniew on 2012-02-20
Actually there is a trashcan and users get used to it quite quickly.... they simply open up the file manager (pcmanfm)   which is an icon i place on the desktop which more or less represents the "computer" icon on windows..... 

They can see whats in the trash and right click empty from there.... its really not a show stopper once you know where it is... is one click away


[Here is a Screenshot]("http://picpaste.com/trashfilemanager-gFcbM2Qd.png")

---

### Post by AleveSicofante on 2012-02-20
For starters, you can't imagine how finicky some users are regarding a new system.

But most of all, a trashcan is not there just to be visible. It's about dragging items into it for temporary deletion. That's the metaphor that originated the function. Hiding the trashcan inside a file manager windows defeats its original purpose.

I hope the LXDE devs understand this and put a trashcan on the desktop.

Regarding the home folder, I agree that putting a PCManFM icon on the desktop might do the trick. However, one of the nice things about a true home folder icon is -again- its ability to use drag and drop on it. It's not a problem for migrating users from Windows though (the "My PC" icon doesn't accept drag and drop either).

---

### Post by SteveDee on 2012-02-20
Trash-can!...Show-stopper?...come on guys, get a life!

I hope the devs don't take you seriously and waste valuable time on this, when they should be fixing bugs, driving down boot time and RAM usage.

Lubuntu/LXDE is all about speed and low resources. There are plenty of Linux distros out there which can provide trash-cans, drag & drop everywhere and other tedious features for those that want them.

---

### Post by MG&amp;TL on 2012-02-20
> **SteveDee said:**
> Trash-can!...Show-stopper?...come on guys, get a life!


Heh, heh. I agree, but the devs have made it substantially easier to place stuff on the desktop. We have a nifty-right click menu in 12.04 now. :)

---

### Post by AleveSicofante on 2012-02-20
> **SteveDee said:**
> Trash-can!...Show-stopper?...come on guys, get a life!

I hope the devs don't take you seriously and waste valuable time on this, when they should be fixing bugs, driving down boot time and RAM usage.

Lubuntu/LXDE is all about speed and low resources. There are plenty of Linux distros out there which can provide trash-cans, drag & drop everywhere and other tedious features for those that want them.
Oh, I had forgotten that I was on a Linux forum.

Excuse me for having an opinion on design.

Please never leave your linuxy style and keep living that interesting life of yours.

I guess I'll keep those users on the speedy, low-resource and user friendly Windows XP.

---

### Post by MG&amp;TL on 2012-02-20
> **AleveSicofante said:**
> Oh, I had forgotten that I was on a Linux forum.

Excuse me for having an opinion on design.

Please never leave your linuxy style and keep living that interesting life of yours.

I guess I'll keep those users on the speedy, low-resource and user friendly Windows XP.

Hey, you're on a linux forum. He didn't mean malice (nor did I) but we had differing opnions. As linux nerds, we express that in the only way we know how, sarcasm and light flaming. As you're doing now (well...the sarcasm bit, anyway). Ubuntu Forums is quite a nice place, really, you just have to learn to dodge the flame. :)

Have a nice day, and use whatever works for you. Why don't you submit your idea to the Ubuntu brainstorm, ping it on the mailing list, or even better, implement it (if you have  the skills, that's great, if not, if it does get used, it will get done slower) and submit it. Never know, might get done. :)

---

### Post by ronniew on 2012-02-20
you can drag and drop your files to the trashcan located in the filemanager..... you also right click on it to empty.

its simply not on the desktop but in the filemanager... other than that its the same

try out lubuntu and how the trash works maybe you'll find its not bad its just a little different.


As for XP 
speedy and low resource was lost with sp3 but also its just friggin old full of security holes and troubled with viruses, spyware, adware, malware, trojans you name it....   lubuntu is at least todays software without the other junk that comes with the "user friendly" windows world.

---

### Post by billathome65 on 2013-10-26
I know this is an old thread but just want to say thanks I finally got a trash can on my desktop

---

### Post by wildmanne39 on 2013-10-26
Thread closed. Please do not post in old threads.

---

