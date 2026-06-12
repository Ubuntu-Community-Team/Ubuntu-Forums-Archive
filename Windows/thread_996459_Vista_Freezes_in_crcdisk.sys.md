---
title: "Vista Freezes in crcdisk.sys"
date: 2008-11-28
forum: Windows
---

### Post by melenor on 2008-11-28
Alright i have a notebook that i duel boot with ubuntu and vista for awhile now, i have to use vista for school. but i had to do a force shutdown yesterday with vista and now it will not boot, i was able to attempt a boot into safe mode but on the loading files screen it frooze at crcdisk.sys i have waited over an hour with no change. I have had good luck here getting help but on any other windows forum they always treat you like your really dumb and most of the time you never get an answer which is why i posted here because i think i could actually get a response and help that I would not receive elsewhere.

---

### Post by hansdown on 2008-11-28
Hi melenor.

Have you had a windows update lately?

Some microsoft updates look for the master boot record (mbr).

If it does not find the mbr, which is overwritten by the grub boot loader, it may cause havoc.

[http://forum.notebookreview.com/showthread.php?t=201724](http://forum.notebookreview.com/showthread.php?t=201724)

---

### Post by melenor on 2008-11-28
that is not the problem i can boot into ubuntu and windows (kinda). but when i boot into windows it freezes at the loading bar, if i choose boot into safe mode, it shows what is being loaded and it freezes at "Loading : crcdisk.sys" it has nothing to do with ubuntu. but Vista and crcdisk.sys.

---

### Post by Battie on 2008-11-29
Unfortunately, the last driver named in that list may not be the problem driver.  It might be the last driver that was successfully loaded before the problem started.

Have you tried Last Known Good Configuration?  That option is more likely to solve boot-up BSODs, but it won't hurt anything to try it.

---

### Post by tommynz1975 on 2008-12-03
A few threads exist on this topic some hope to help others leave me confused...  I have a compaq lappy with same issue that I have never fixed.

let us know when you find the answer.

---

### Post by CholericKoala on 2008-12-03
I have never seen an answer to this problem before.  I have wanted to try something that seems like it would work though:  chkdsk /p /r

Or maybe, taking the drivers from an existing, functional system.

One thing that only worked once was doing a manual restore copying over saved hive files.  I'd try the others first though.

---

