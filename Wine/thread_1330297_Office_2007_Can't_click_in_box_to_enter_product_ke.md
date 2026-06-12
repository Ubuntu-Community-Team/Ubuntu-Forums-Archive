---
title: "Office 2007: Can't click in box to enter product key"
date: 2009-11-18
forum: Wine
---

### Post by Charles Dexter Ward on 2009-11-18
This only happens with my desktop computer. In addition to not being able to click in the box to enter the product key, I also cannot read the EULA with Office and other programs. I suspect it has something to do with the ATI fglrx video driver I'm using. I was able to enter the key by copying the ProductID registry entry from another computer and importing it, but I would rather know how to fix the problem.

Any ideas? Thanks in advance.

---

### Post by TristanCharles on 2011-01-24
I also am having this problem. Currently have it running in a trial until I can figure it out...

---

### Post by roemhildtg on 2011-05-21
I had this exact problem, I uninstalled the programs completely, removed the wineprefixes and reinstalled and it worked out.

---

### Post by jjb2011 on 2011-06-29
2 years later: Ubuntu 11.04 and trying to port Office 2007 with POL. Won't work. Can't enter key. Help! I'd totally switch but I'm a writer and teacher and need Word/PPT. 

Thanks in advance!

---

### Post by Hank_The_Dog on 2011-07-02
Really?

Open Office?

Why would you even try to use a MS product... bleh...

Just use OpenOffice.Org

in Ubuntu....

(Should already be installed)
1. Go to The Ubuntu Software Center
2. Search for 'OpenOffice.Org'
3. Click Install next to what you want

or

run this is the terminal

[I]sudo apt-get install openoffice.org
[/I]
Please donate if you can, but OpenOffice has little migration issues... I think it goes all the way back to before windows95... This means you should be able to open pretty much anything and save it in whatever format you desire...

Enjoy Open Source Software responsibly...




But if you still insist on using Microsoft's 'Wonderful' Products, and paying for a CD Key... then please continue to read this...

[http://ubuntuforums.org/showthread.php?t=1173365](http://ubuntuforums.org/showthread.php?t=1173365)

or...

[http://www.unixmen.com/linux-tutorials/421-install-ms-office2007-on-ubuntu-using-playonlinux](http://www.unixmen.com/linux-tutorials/421-install-ms-office2007-on-ubuntu-using-playonlinux)

---

### Post by jjb2011 on 2011-07-02
Got it to work with PlayOnLinux. Go figure. 

Open Office? I prefer LibreOffice, particularly now that Google is behind it. There is now hope (they did fund Firefox and Chromium, after all, and Ubuntu users use them, right?). 

I used to be a WordPerfect user (I'm a writer, FYI). But Office 2007 ribbon is not just "nice looking," it simplifies finding things. Plus there are add-ins for Office 2007 that don't exist for Oo (Office Tabs, for example). A tabbed interface is USEFUL when you have 4-5 documents open (perhaps 3 versions of my resume to be updated, then two other documents). The old way of hunting at the bottom isn't the same. 

Lastly, I WANT to prefer Oo and LO but there are endless annoyances: in Office 2007 you can customize the quick tab and add things like "Hanging Indent" button (I use a lot). I went through the Libreoffice help and their "Hanging Indent" feature basically involves MANUALLY resetting indent sizes each and every time. WTF? In MS Office, I just hit the button and it does it automatically. 

Besides, as an educator I can buy 5 licenses of Office 2007 or 2010 Pro for $10 ($2 per computer). So no need to save money. Even so, I _would_ if Oo or LO were equal to MS Office but they aren't -- yet. Let's hope Google works its magic! 

(As I recall, some things -- like track changes -- don't always carry from Open Office to another person's MS Office. That's a deal breaker. 

But I'll keep checking back - and hope spring eternal. Mac revived from the dead, in part, by encouraging people to use MS Office. Open Office has caught up with Office 2000 or 2003 (maybe) but not 2007 or 2010. The world moves and Open Office stood still. 

IMHO.

---

### Post by Hank_The_Dog on 2011-07-02
jjb,


Glad you got it up an running...

Touche.

Happy writting!!!:)

---

### Post by EdwardViesel on 2011-09-06
... just for the record and because it happened to me today:

Some applications need extra "overrides" in the Wine configuration ("Libraries"). If you add these *before* activating your Office 2007, you won't be able to enter anything into the product key field.

It's just something that happens...

Solution: simply "delete" the override(s), restart Office 2007, enter the product key, add the override(s) again in the Wine configuration.

Thanks to rygar:

[http://ubuntuforums.org/archive/index.php/t-1283792.html]("http://ubuntuforums.org/archive/index.php/t-1283792.html")

---

### Post by aDragonfly on 2011-11-17
Aha!  Thank you Edward, that worked!

---

