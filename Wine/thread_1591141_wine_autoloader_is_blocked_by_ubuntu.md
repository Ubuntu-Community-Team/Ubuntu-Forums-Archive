---
title: "wine autoloader is blocked by ubuntu"
date: 2010-10-08
forum: Wine
---

### Post by jimmybarcelona on 2010-10-08
I'm trying to install a language program on my computer to learn French. Whenever I try to open either setup.exe or autorun.exe ubuntu says that the files are not marked as executable because they came from an untrusted system. A cd is a read only file system, so i cannot change the executable bit. How can I install this program from a CD?

---

### Post by Gunman1982 on 2010-10-09
Have you installed wine? Are you starting the setup.exe with wine?

---

### Post by e79 on 2010-10-09
If WINE is giving you problem from the CD itself, I would suggest you to copy the whole content of the CD in a folder in your **/home/user** directory, right-click the .exe and mark it as '**executable**'. You should then be able to install it under WINE.

Hope this helps

---

