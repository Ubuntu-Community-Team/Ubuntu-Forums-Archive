---
title: "mounting external drive"
date: 2018-05-27
forum: Ubuntu/Debian BASED
---

### Post by Lloydb39 on 2018-05-27
Using Elementary OS on this old laptop. Trying to mount an external drive. It shows the drive but won't mount. The drive was the boot drive for a Windows system that was trashed by the update to Win 10 (long story). Anyway, I REALLY need to get some files off of it, namely my Thunderbird address book, which has ALL of my contacts.  It won't mount automatically, saying it isn't clean, etc. I'm thinking there must be a terminal command that will let me mount the drive and access the files, but I don't know what it is. Can anyone help?

---

### Post by TheFu on 2018-05-27
I don't know what, if any, commands will work, but the file system was left open. Linux won't mount it until the file system is closed.  You need to find a way to do that.  Usually for things like this, I'd suggest using a Windows machine.

---

### Post by yancek on 2018-05-27
If you can't boot your windows install, the best option is suggested above, using another windows machine to fully shut down.  That might work  You might try using ntfsfix on the windows partition which can sometimes do some very minor repairs on a windows filesystem.  I wouldn't hold out much hope though.  Doing an online search or going to a windows forum to search for similar problems or post your own thread there would probably be more useful than posting here.

---

