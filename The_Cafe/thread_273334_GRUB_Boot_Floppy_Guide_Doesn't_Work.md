---
title: "GRUB Boot Floppy Guide Doesn't Work"
date: 2006-10-07
forum: The Cafe
---

### Post by user1397 on 2006-10-07
this guide: [https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy), did not work for me.  one thing i noticed is that it says to copy over stage1 and stage2, but i saw something like stage1.5 , so...wtf

i wanted to make one as a backup to my ever changing hard-drive:p

---

### Post by user1397 on 2006-10-10
do you guys think this guide is outdated?

---

### Post by user1397 on 2006-10-11
nothing?  :(

---

### Post by confused57 on 2006-10-11
Maybe this howto will work:
[http://www.ubuntuforums.org/showthread.php?t=224345](http://www.ubuntuforums.org/showthread.php?t=224345)

---

### Post by user1397 on 2006-10-14
> **confused57 said:**
> Maybe this howto will work:
[http://www.ubuntuforums.org/showthread.php?t=224345](http://www.ubuntuforums.org/showthread.php?t=224345)thanks man, that worked

---

### Post by kenmonk on 2007-07-20
I  have just spent an hour (or two) fighting exactly this problem.  Following some of the other links and trying what was suggested didn't work - but I did spot something.

Some one gave a listing of their 'devices.map' file.  The top line read '(fd0) /dev/fd0'.  Mine on the floppy didn't have this, so I added it and did the 'root ... setup again and rebooted.

The result - one working boot floppy!!

Hope this helps.

It also shows how easy it is to assume that everyone will have exactly the same setting in all the relevant files.  Perhaps posters should be aware of this ans list the contents of ALL associated files when describing such setup tasks.  It might just save a lot of frustration!!??    :-)

---

### Post by user1397 on 2007-07-20
> **kenmonk said:**
> I  have just spent an hour (or two) fighting exactly this problem.  Following some of the other links and trying what was suggested didn't work - but I did spot something.

Some one gave a listing of their 'devices.map' file.  The top line read '(fd0) /dev/fd0'.  Mine on the floppy didn't have this, so I added it and did the 'root ... setup again and rebooted.

The result - one working boot floppy!!

Hope this helps.

It also shows how easy it is to assume that everyone will have exactly the same setting in all the relevant files.  Perhaps posters should be aware of this ans list the contents of ALL associated files when describing such setup tasks.  It might just save a lot of frustration!!??    :-)Ah, thanks for knowledge :)

---

