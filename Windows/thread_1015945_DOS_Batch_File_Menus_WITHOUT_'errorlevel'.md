---
title: "DOS Batch File Menus WITHOUT 'errorlevel'"
date: 2008-12-19
forum: Windows
---

### Post by james_xxx on 2008-12-19
I am rather embarrassed to resort to asking about this in the Ubuntu Forums, but... 

I have the task before me of writing a rather lengthy MSDOS batch script that uses interactive menus. 

(I will add that I have primarily done this assignment using FreeDOS running in VirtualBox, or using dosemu :D .)

I spent nearly a day writing (what I thought was) a very nice script, only to discover that using 'if errorlevel' will not be an option. Unfortunately, this is what I had initially used throughout.

I have scoured a book on MSDOS and numerous online tutorials, but every example of a batch file menu I can find, uses this command.

I am wondering if anyone out there in Ubuntu-land would have an idea as to how to create interactive menus in DOS _without_ using 'choice' and 'if errorlevel'.

Suggestions will be VERY MUCH appreciated.

Thanks!

---

### Post by james_xxx on 2008-12-19
OK, I figured out what was going wrong for me.

I had been testing my batch file in the DOS that comes with Win98, and the method I had used as an alternative to 'if errorlevel' was NOT working in that version of DOS. 

What I am using now is 'set /p variable=', which is working well in dosemu, and I believe will work well in MSDOS 6.22. I will find this out for sure shortly.

---

