---
title: "Wine &amp; Sequence Publishing software"
date: 2011-01-26
forum: Wine
---

### Post by cpgos on 2011-01-26
I would appreciate some help in getting a package called "The Sage" from Sequence Publishing to run, see [http://www.sequencepublishing.com/thesage.html](http://www.sequencepublishing.com/thesage.html).

I am using Ubuntu 10.04LTS and have Wine v1.2 installed and the location of the file that I need to execute is on the path, see below:

coastal@asus-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/coastal/.wine/drive_c/P*/TheSage

However when I try to run TheSage.exe using "wine TheSage" a message is displayed about a missing file, tsi.dat, which is in the same location as the file that I need to run, see attached screen dump.

A listing of the relevant directory and terminal output follows below.

Best regards,
cpgos

coastal@asus-laptop:~$ cd /home/coastal/.wine/drive_c/P*/TheSage

[email]coastal@asus-laptop:~/.wine[/email]/drive_c/Program Files/TheSage$ ls
Help  license.txt  MFC42.DLL  mfc42u.dll  TheSage.exe  tsi.dat  Uninstall.exe

[email]coastal@asus-laptop:~/.wine[/email]/drive_c/Program Files/TheSage$ wine TheSage
err:clipboard:ChangeClipboardChain hWndViewer is lost
fixme:keyboard:UnregisterHotKey (0x1005e,45037): stub
[email]coastal@asus-laptop:~/.wine[/email]/drive_c/Program Files/TheSage$

---

