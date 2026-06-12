---
title: "Securely Erase Console History/Browsing History/Recently Accessed etc"
date: 2008-05-23
forum: Security
---

### Post by Freeparty on 2008-05-23
I would like to try and set up a script to securely erase files relating to Console history, Browsing History (firefox), Recently Accsessed Programs/files/documents and swap file contents when a user is logged off or the workstation is shut down.

I suppose I am asking there a program akin to Evidence Eliminator for windows or something like that for linux? If not i would like to try making a bash script which uses the 'wipe' program to achieve the above.

Could anyone point me in the right direction for what directories or files need to be wiped?

Also interestingly enough i tried turning off the console history and it still saves alot of previously typed commands, has anyone else ran into this before?

Thanks in advance

---

### Post by hyper_ch on 2008-05-23
Well, ext3 is a journaled filesystem so there might be pieces in a few places...

Have a look at this discussion with regard to safely erase:  [http://ubuntuforums.org/showthread.php?t=797252](http://ubuntuforums.org/showthread.php?t=797252)

---

### Post by Freeparty on 2008-05-28
I actually installed ubuntu using ext2 partitions so without the journaling. Thanks for the link to the thread though.

I suppose what I was after was something like 'Where is the console history and recently accessed documents etc stored?' as in where are the directories/files I need to erase.

---

### Post by hyper_ch on 2008-05-28
dunno where there's overall some data... as I fully encrypt my system I'm not bothered with that anymore...

However the other thread mentioned has some clues about things to look for - if I remember correctly.

---

