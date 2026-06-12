---
title: "checksum takes forever after burning ISO image"
date: 2012-04-08
forum: Ubuntu Studio
---

### Post by raymondvillain on 2012-04-08
Would like to know if anyone else has had this problem.

Downloaded Ubuntu Studio 11.10 (for amd 64 bit processor) and went through the steps to burn it on a DVD.  The box sez "100% complete" and then it starts creating the checksum.  Here is where it gets lost, I think.  The DVD drive clicks away and the estimated time to completion slowly goes up to 1 hour, 2 hours, 3 hours, etc.

Am I doing something wrong?

---

### Post by jejeman on 2012-04-08
Which software are you using for burning?

---

### Post by raymondvillain on 2012-04-08
jejeman asked what software I used for burning.

I didn't choose anything, when the DVD was inserted a box appeared asking what I wanted to use.  I closed this box, right clicked on the .iso file, and selected "write to disc".

Not sure what the program was that actually burned the disc.

Does this help?

---

### Post by jejeman on 2012-04-09
If you are using Ubuntu, then it's probably Brasero. Open Brasero, and go to Edit>Plugins. Uncheck the checksum plugins. See if that helps.

---

