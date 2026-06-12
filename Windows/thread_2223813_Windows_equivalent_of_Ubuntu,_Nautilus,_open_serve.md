---
title: "Windows equivalent of Ubuntu, Nautilus, open server with sftp"
date: 2014-05-13
forum: Windows
---

### Post by squakie on 2014-05-13
I've made and set up several media centers using Raspberry Pi's and OpenELEC.  In Ubuntu I can connect to the Pi's via ssh from the command line, and in Windows via Putty.  In addition I can access the Pi's in the Nautilus file manager by "Open Server" and sftp to the Pi's IP.  One of those Pi's I have given to my sister and brother in-law.  They run Windows 7 (I run Ubuntu 14.04 and Windows 8.1).  I need a way in Windows to duplicate the Nautilus option in Ubuntu so they can drag/copy files from their PC to the Pi.  They will need to be able to do this when they add new media files and need them copied to the Pi.  I need to keep it as simple as possible for them.

Thanks!

---

### Post by squakie on 2014-05-13
Found something called filezilla which seems to be cross-platform and seemed to work.  I got write errors on the output at 10mb, so I don't know if I'm doing something wrong or if perhaps my remote Pi's external hard disk is failling.

---

### Post by mastablasta on 2014-05-15
yeah filezilla is excelent FTP client and server.

otherwise windows explorer works just fine.

others good ones that come to mind are TotalCommander and Free Commander if one prefers the Nnorton Commander interface. midnight commander for cli afficionados.

by the way how did you install the sftp server? in openelec. i mean which one? is there something in addons? i have an older winxp mashicne that for some reason can't access the Pi via samba. linux and win7 pc have no issues accessing it. i can also access linux from winxp, but not P. eventhough i tried various settings. so i am thinking if i could get a light ftp on it it might help. also i haven't upgraded the openelec yet. waiting for bugs ot be ironed out :D

---

