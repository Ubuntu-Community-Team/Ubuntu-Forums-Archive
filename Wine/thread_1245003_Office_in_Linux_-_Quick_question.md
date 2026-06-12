---
title: "Office in Linux - Quick question"
date: 2009-08-20
forum: Wine
---

### Post by Ascendancy117 on 2009-08-20
So I'm dual booting linux and windows. I already have Office 2007 installed on my mounted ntfs partition. Is it in anyway possible to use wine or another method to use that installation in linux? I don't have enough disk space to install it again on my linux partition but would like to use it in linux because OpenOffice doesn't display a lot of my old word documents properly. 

I tried just opening the .EXE files, and it told me that IOPL wasn't enabled

---

### Post by pmlxuser on 2009-08-20
try using virtual machine, install windows and install office you can then use it from within linux.

---

### Post by Ascendancy117 on 2009-08-20
Could you be a little more specific? What virtual machine do you recommend, and what do you mean by installing windows and office on them? I already have windows and office installed (on another partition) and i'm trying not to install them again.

---

### Post by darkmire on 2009-08-20
I think I get what your're trying to say and that is -* can I use my version of Office 2007 on my Windows partition from my Linux partition because I don't have enough space to install it again on my Linux partition?*   The answer is no - your Office 2007 installation on your Windows Partition is installed for Windows and can't be run from another OS elsewhere - it has to be installed on your Linux partition for you to use it on your Linux partition.

This is one of the fundamental weaknesses of running Linux and Windows in separate partitions.   I did as most Linux users who have Windows programs they don't want to give up, and that is to run Linux exclusively on my hard disk.  I then install Virtualbox in Ubuntu and then ran Windows in a virtual machine and installed my windows stuff there.  Windows stuff runs seamlessly in Linux in either windowed or seamless.  I've always found this a more stable and less problematic way of running Windows stuff than Wine, with or without Crossover.

---

### Post by Grenage on 2009-08-20
Out of curiosity, what would stop **Ascendancy117** from using a symlink from the wine directory to the installed directory (assuming critical DLL references are in the wine system folders)?

---

### Post by Ascendancy117 on 2009-08-21
Um i don't know... haha

I'd be willing to try it, but i don't know how.

---

### Post by Jon Monreal on 2009-08-21
> **Grenage said:**
> Out of curiosity, what would stop **Ascendancy117** from using a symlink from the wine directory to the installed directory (assuming critical DLL references are in the wine system folders)?

I would assume that the problem with this might lie with the registry and steps Microsoft may have taken to help ensure that not even Windows can run Office from another partition.

---

### Post by DoktorSeven on 2009-08-21
Yes, Office is kind of a system-level install within Windows; you would have to install the whole thing under Wine separately to have any chance of it working, unless you want to take the time to hunt down exactly what is installed where, what registry keys are needed and adding them, etc, that *might* get it working, which would be a huge undertaking if even possible.

---

### Post by NightMKoder on 2009-08-22
With wine it's easy, considering registry files are plaintext. Just do something like

```

export WINEPREFIX=/tmp/wine_test
mkdir $WINEPREFIX
wine notepad # close notepad

export WINEPREFIX=/tmp/office_test
mkdir $WINEPREFIX
wine /media/cdrom/Setup.exe #install office

diff -r /tmp/wine_test /tmp/office_test > office_install.diff

```

This won't quite capture the contents of dlls though, but it will give you an idea of what text files get changed.

---

### Post by Jon Monreal on 2009-08-22
> **NightMKoder said:**
> With wine it's easy, considering registry files are plaintext. Just do something like

```

export WINEPREFIX=/tmp/wine_test
mkdir $WINEPREFIX
wine notepad # close notepad

export WINEPREFIX=/tmp/office_test
mkdir $WINEPREFIX
wine /media/cdrom/Setup.exe #install office

diff -r /tmp/wine_test /tmp/office_test > office_install.diff

```This won't quite capture the contents of dlls though, but it will give you an idea of what text files get changed.

Even if he were to get the registry entries, he would have to change them so they point to the installation on the Windows drive. This sounds like an awful lot of work for something that might not work correctly. Now, there are a couple of programs (Outlook and Access) that don't work under Wine, so if you (Ascendancy117) want those to work, you will have to either use a VM or (gasp!) Windows itself at the moment. If you have the time and patience to try this, however, it would be interesting to see if it works.

---

