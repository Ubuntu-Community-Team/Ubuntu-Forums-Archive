---
title: "Windows 7 64Bit - Adding folder outside home DIR issue."
date: 2012-01-29
forum: Ubuntu One (CLOSED)
---

### Post by Nicky.. on 2012-01-29
Hi all,


Am having a issue with the windows Ubuntu One Client, When i click add folder to sync if i choose any folder outside my home DIR i get this error.  

*"The chosen directory "H\backup\files" is not valid, Please choose a folder inside your "home dir"  *

Is there anyway to get around this as i do not want to have to move my files from my backup drive to my home dir this is really a pain for me am thinking about buying more storage but not until am able to solve this issue.

Ps. I've tried running the client as admin but makes no difference.

Thank you.

---

### Post by ajgreeny on 2012-01-29
I doubt that the ubuntu-one system can understand that pathway.  Backslashes are used differently in linux and ubuntu.

For the pathway to your files you will need to use the pathway of the partition mountpoint in your ubuntu OS, eg */media/windows/backup/files* or whatever it happens to be.  That assumes the operation itself is possible for non /home folders etc etc, and not using ubuntu-one, I can not help you there.

---

