---
title: "e-sword problems (sorry - long post)"
date: 2007-05-14
forum: Ubuntu Christian Edition
---

### Post by curious_human on 2007-05-14
I'm using Ubuntu 7.04 Feisty Fawn AMD64.
I have wine 0-9-37 installed and running nicely.
I downloaded the esword-ubuntu_1.6_all.deb and installed that with dpkg.
I select 'Applications->Accessories->e-Sword Installer' click 'OK' and nothing seems to happen.
So I cd /usr/local/apps/esword4linux and the do a ./install and get the following output

--17:06:42--  [http://www.whatwouldjesusdownload.com/.online.key](http://www.whatwouldjesusdownload.com/.online.key)
           => `.online.key'
Resolving [www.whatwouldjesusdownload.com](www.whatwouldjesusdownload.com)... 70.86.39.210
Connecting to www.whatwouldjesusdownload.com|70.86.39.210|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 32 [text/plain]

100%[====================================>] 32            --.--K/s             

17:06:43 (3.39 MB/s) - `.online.key' saved [32/32]

--17:06:43--  [http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE](http://download.microsoft.com/download/d/1/3/d13cd456-f0cf-4fb2-a17f-20afc79f8a51/DCOM98.EXE)
           => `DCOM98.EXE'
Resolving download.microsoft.com... 1.0.0.0
Connecting to download.microsoft.com|1.0.0.0|:80... 

After a few minutes I get the following error message

"There seems to have been an error. You will need to run the e-Sword Installer again. This is not uncommon and is usually due to a problem downloading some of the needed files."
And in my term window I see

failed: Connection timed out.
Giving up.

Now this is odd. I have located DCOM98.exe on Microsoft's site (I use Firefox) but I cannot download the file. At least, I can't download it from Linux! I can download it from Windows XP (with both IE7 and Firefox).

So, I went to plan 'B' which is a manual install of e-sword.
This works fine to begin with. The problem is when I try to install modules. I copy a module to

/home/matt/.wine/drive_c/Program\ Files/e-Sword/

then cd to the above dir and wine <module-name>. This appears to hang, but it is actually working, ableit painfully slowly. There's no way I could install all the modules this way.

Any ideas?

Matt



ADDITIONS

So I've solved this problem.
I simply copied my entire e-sword directory over from windows and things seem to be working fine.

---

### Post by tak1150 on 2007-05-14
If you copy the actual module files from Windows to the e-sword directory in wine, it should work (it did for me).

ie, copy
Windows:
c:/Program Files/e-Sword/STUFF
to
Linux:
/home/user-name/.wine/drive_c/Program\ Files/e-Sword/

In other words, you'd have to install the modules under Windows and copy the installed files in "e-Sword"

Hope this helps.

---

