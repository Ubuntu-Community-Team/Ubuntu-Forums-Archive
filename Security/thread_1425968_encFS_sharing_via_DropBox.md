---
title: "encFS sharing via DropBox"
date: 2010-03-09
forum: Security
---

### Post by PalapaGuy on 2010-03-09
I set up encFS on two computers using the same password and same directory names and paths on each computer.  When I uploaded encrypted files to DropBox from either computer I could see and decrypt the files on the same computer that uploaded  them.  But neither computer showed the files uploaded to DropBox from the other computer.  

Looking at the DropBox Website with a browser showed the files present from both computers as it should have, although of course they were encrypted.

Any idea what's preventing me from sharing the files between computers?

Thanks.

---

### Post by The Cog on 2010-03-10
I wonder it it's that the virtual filesystem thinks it's fully in charge of the enctrypted set and simply isn't expecting to see the encrypted files appearing and disappearing on their own. Have you tried unmounting and remounting encfs to see if that makes it learn of their existence?

---

### Post by chronos00 on 2010-07-23
Hi!

I am having the exact same situation and I'm arriving the the same obstacles.
Were you able to solve the DropBox encryption problem?

Thanks in advance.

---

