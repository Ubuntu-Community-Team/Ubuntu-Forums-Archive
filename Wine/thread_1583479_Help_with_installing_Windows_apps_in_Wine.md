---
title: "Help with installing Windows apps in Wine"
date: 2010-09-27
forum: Wine
---

### Post by Aelanna on 2010-09-27
I am a Windows user who is FINALLY making the attempt to switch to Linux. I'm a computer tech who's been in the field long enough that I know DOS commands and the basics of how to do some things in Terminal, but this is my first real attempt to try to move and see if I can do my everyday things in Linux.

I have some older Windows apps that I MUST be able to run in order to do my work. I understand I need to use Wine or some kind of virtual machine to run these apps. Currently I'm using Windows XP.

I set up a second machine to test out Linux and wine and see if my apps will run. So far, very little luck. I am using Ubuntu 10.04 Desktop and whatever version of Wine that's in the Ubuntu Software Center. 

These are the apps I NEED to run:

Office 97 (Excel and Access only), Office 2000 (Excel and Access only), Visual Basic 6. 

I managed to successfully install and run VB 6, but have not been able to get Office 97 to install.  I've tried running Wine with Windows XP emulation and Windows 98 emulation without success. When I run the install for Office 97, everything looks fine until I get to the screen where it starts copying files. The blue line zips across the screen without doing anything that I can tell, and then instead of the windo saying install was successful I get one that says the install was unsuccessful with no explanation as to why. 

Do I need to use an older version of Ubuntu/wine, or is there some trick to getting it to work? Any help would be appreciated.

---

### Post by Tibuda on 2010-09-27
Not every application works perfectly with Wine. Search [http://appdb.winehq.org/](http://appdb.winehq.org/) for your apps to see other user experiences with them.

EDIT: Out of curiosity: why do you want to install such old version of Office?

---

### Post by Aelanna on 2010-09-27
Because my work requires it. All the databases I use are Access 97 (about 90%) and the rest are Access 2000. Same with the spreadsheets we use. 

I think I've installed and uninstalled Wine so many times it no longer functions. I can't run winecfg any more without getting a bunch of errors about missing dlls. I will check out that link, thanks.

---

### Post by Tibuda on 2010-09-27
> Because my work requires it. All the databases I use are Access 97 (about 90%) and the rest are Access 2000. Same with the spreadsheets we use.I see. The 97 files would not work on more recent versions of Offcie?

Backward compatibility is one of the strong points of Microsoft over Linux.

> I think I've installed and uninstalled Wine so many times it no longer functions.
Maybe your ~/.wine folder got corrupted. Try to rename it and run winecfg again.

---

### Post by dankegel on 2010-09-29
> **Aelanna said:**
> I have not been able to get Office 97 to install.  I've tried running Wine with Windows XP emulation and Windows 98 emulation without success. When I run the install for Office 97, everything looks fine until I get to the screen where it starts copying files. The blue line zips across the screen without doing anything that I can tell, and then instead of the windo saying install was successful I get one that says the install was unsuccessful with no explanation as to why. 


There's a problem installing Access '97:
[http://bugs.winehq.org/show_bug.cgi?id=3689](http://bugs.winehq.org/show_bug.cgi?id=3689)
and I'm not aware of a solution.

You might want to try the commercially supported variant of
wine, Crossover: 
[http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)
All revenues from that are plowed back into Wine development,
and it has had a lot of polish on Microsoft Office 97 and 2000.

---

