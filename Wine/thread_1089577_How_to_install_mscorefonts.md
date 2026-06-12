---
title: "How to install mscorefonts?"
date: 2009-03-07
forum: Wine
---

### Post by wolfyking2 on 2009-03-07
How would you do this.  I heard it's in winetricks, so I downloaded winetricks but it wasn't in their.  I need mscorefonts to play conquer online, because it needs the font Courier 12.  It doesn't have to be mscorefonts actually, I just need Courier 12 font.

---

### Post by Therion on 2009-03-07
This should do it:```
sudo apt-get install msttcorefonts
```
I don't know that you can install them (the Microsoft fonts) individually.

Edit:  Just found this, though it's an .exe file.  Maybe since you need it IN Wine it will work?  I'm not a wine user...

[http://sourceforge.net/project/downloading.php?groupname=corefonts&filename=courie32.exe&use_mirror=voxel](http://sourceforge.net/project/downloading.php?groupname=corefonts&filename=courie32.exe&use_mirror=voxel)

---

### Post by howefield on 2009-03-07
Ensure you have multiverse repository enabled in your software sources.

Then either install msttcorefonts via synaptic package manager or install via the terminal
```

sudo apt-get install msttcorefonts
```

---

### Post by wolfyking2 on 2009-03-07
Darn, it says I already have it installed.  How can I get the Courier 12 font?  I need it to play conquer online

---

### Post by Therion on 2009-03-07
Did you see my edit?  Don't know if that will work or not...

---

### Post by wolfyking2 on 2009-03-07
nope, it didn't work.  although, it said to go to regedit, HKLM/software/fonts and add courier 1.  I got there, but I'm not sure how to add another thing in the folder.

---

### Post by blackened on 2009-03-07
Could you not copy and paste Courier from /usr/share/fonts to c:\Windows\system32\fonts since you have msttcorefonts installed?

I think that would work, been a long time since I've really dug in Windows so YMMV.

---

### Post by wolfyking2 on 2009-03-07
Well, I got the courier thing, arial and simsun fonts (following this HOWTO:[http://ubuntuforums.org/showthread.php?p=4560835#post4560835]("http://ubuntuforums.org/showthread.php?p=4560835#post4560835"))  So I got the other DLLs in the system 22, and did everything it said, but it still is stuck at the loading... part.  Although when I went to winecfg, libraries, and the 2 DLLs that begin with an m (forgot what they're called, just look in the howto) weren't there.  So maybe I'll fix that and see if it works.

---

### Post by binbash on 2009-03-07
google > winetricks and install via it

---

### Post by chris.olive on 2009-03-08
> **wolfyking2 said:**
> How would you do this.  I heard it's in winetricks, so I downloaded winetricks but it wasn't in their.  I need mscorefonts to play conquer online, because it needs the font Courier 12.  It doesn't have to be mscorefonts actually, I just need Courier 12 font.
I had the same problem solved it by loading KDE desktop in system there is a font loader, download fonts to a file on your disk then useing font loader go to this file and load.
I normaly run Gnome desktop but found this installed the fonts for all programs use.
Chris

---

### Post by Clopper Almon on 2012-03-15
The method of getting the msttcorefonts described here works on Ubuntu 11.10, but you end up having to agree to a long MS End User License Agreement. That is all right except that there is no obvious way to agree to it! 

I finally stumbled on the key: tap the Tab key. Then the <Yes> shown on the form is highlighted and you can agree.

It is a bit simpler to go through the Ubuntu Software Center and search for the ttf-mscorefonts-installer and use it. 

Also remember to log out and then log in again before trying to use the fonts.

---

### Post by howefield on 2012-03-15
Let old threads sleep.

Closed.

---

