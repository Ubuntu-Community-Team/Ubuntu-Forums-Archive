---
title: "Nautilus not generating thumbnails for pictures on network shares"
date: 2013-04-27
forum: Ubuntu, Linux and OS Chat
---

### Post by emptythevoid on 2013-04-27
Nautilus is not generating thumbnails for pictures on network shares. This happens specifically when connecting to the share using the network browser (which uses gvfs). I have *no* problem when I connect using mount -t cifs with uid=<my user name> from the terminal.

First, yes, I have set Files->Preferences->Preview->Show Thumbnails = Always

Second, running Nautilus from the command line and navigating to a directory on the network share will throw up these error messages for the pictures:
(nautilus:7969): GnomeDesktop-WARNING **: Unable to create an input stream for smb://mini9/share/SQAXLY~G.JPG: No such file or directory

Third, I have full read/write privileges on the network share I'm conneced to. The network share is hosted on an Ubuntu 12.10 desktop.

I'm pretty sure I had this same problem with Ubuntu 12.10 and was not able to resolve it other than to mount the network share from Terminal using mount -t cifs.

Any thoughts?

EDIT:  I can double-click on the pictures and open them just fine.

---

### Post by emptythevoid on 2013-04-27
I think the nautilus error is unrelated.

---

### Post by emptythevoid on 2013-05-10
Bump?  Should I file a bug report instead?

---

### Post by screaminj3sus on 2013-05-12
sounds like a nautilus or GVFS bug.

---

