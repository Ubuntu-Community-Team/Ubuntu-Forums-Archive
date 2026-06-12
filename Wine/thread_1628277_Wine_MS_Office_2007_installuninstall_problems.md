---
title: "Wine MS Office 2007 install/uninstall problems"
date: 2010-11-22
forum: Wine
---

### Post by HaydenHaydo on 2010-11-22
So I managed to install Wine and microsoft office 2007, and had it all working, but the version I first downloaded didn't come with OneNote (I'm a student and use this quite a bit). I uninstalled the Standard version and then downloaded another version (Ultimate). However, during the installation, the window says it run into an error and I should look at the log files. I tried going to wine and uninstalling everything that has to do with microsoft office (shows a bunch of MUI programs/files), but when I click on any of them and hit remove, it doesn't do anything, the remove button stays depressed for about 30 seconds, then the MUI just stays there, I cant modify it either. I've also tried going through all my files and deleting everything to do with MS office, and I've purged wine and reinstalled multiple times now.

I'm wondering if there's maybe a cache somewhere where I can remove these files because I'm pretty sure it's what's causing me all my problems.

Help would be greatly appreciated, thanks.

---

### Post by redbook4574 on 2010-11-22
There is one small problem , I don't think onenote works with wine, at least I have never managed to make it work.

---

### Post by Elfy on 2010-11-22
move to wine forum

---

### Post by HaydenHaydo on 2010-11-22
Well I'm not even so much concerned with getting OneNote anymore as just having a working microsoft office, so any help on how to get rid of those MUI files/programs would be great

---

### Post by doctorzeus on 2010-11-22
Some parts of MS Office 2007 don't work on Wine (Power point and Publisher I believe are two) cause of the .NET framework issues I believe,

I only use MS Excel, Access and Word 2007 (all work well) and I use Open Office for the rest...

You could always use free Linux compatible alternatives (this might be just as useful):

[http://nevernote.sourceforge.net/](http://nevernote.sourceforge.net/)

There's lots of similar ones out there, try googling... ;)

Yeah I had that problem to, I seem to remember that I just erased my ".Wine" directory, there's probably better ways but as I didn't have anything else in there at the time..the installers on the original install disks always seemed to work better in my experience..try them and remove all the components...

Note: Purging wine doesn't do anything to fix program problems installed under it, all the config files and programs and everything are held under "/home/(your user name)/.wine/" so deleting this starts a fresh :) , a new one will be created when you open winecfg...

Hope this helps!

---

