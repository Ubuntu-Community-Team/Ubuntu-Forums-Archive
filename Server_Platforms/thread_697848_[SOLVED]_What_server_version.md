---
title: "[SOLVED] What server version?"
date: 2008-02-15
forum: Server Platforms
---

### Post by lncoll on 2008-02-15
After 3 weeks I've finished with a test server (bind, postfix, courrier, mysql, apache) now is working at 100% so next week must install in definitive hardware, an now the question:
What should be better? install version 6.03 LTS and upgrade to 8.10 in a few months,  or install 7.10 an also do the upgrade to 8.04?.
I think that upgrade from 7.10 to 8.04 is less dangerous, but 7.10 is not LTS. Does it mean?:confused:

---

### Post by kevinatkins on 2008-02-15
Hi,

OK, if you were to install 6.06 LTS and then wanted to upgrade to 8.04 LTS, you'd have to upgrade in steps, ie - 6.06 -> 6.10 -> 7.04 -> 7.10 -> 8.04.... lots of messing around! You can't go from 6.06 to 8.04 directly (although I believe that work is afoot to allow direct upgrading between LTS versions - not sure what the position is at the moment)

If I were you, I'd install 7.10 then upgrade to 8.04 maybe a couple of months after it has been released (to allow any bugs to settle ;-)

---

### Post by lncoll on 2008-02-15
Ok, I didn't know that upgrade can't be done direct from 6.06 to 8.04, so you solved all my doubts.
Of course that upgrade to 8.04 must be done al least in  8.06 ;)

---

### Post by Brazen on 2008-02-16
> **lncoll said:**
> Ok, I didn't know that upgrade can't be done direct from 6.06 to 8.04, so you solved all my doubts.
Of course that upgrade to 8.04 must be done al least in  8.06 ;)

You will definately be able to upgrade directly from 6.06 to 8.04.  The LTS releases are better tested and designed for stability than the non-LTS release.  Any serious server admin sticks with the LTS release so I would just get used to that now.

---

### Post by bvidinli on 2008-03-08
You may try Easy Hosting Control Panel for Ubuntu to install all at once... 
see 
[http://ubuntuforums.org/forumdisplay.php?f=180](http://ubuntuforums.org/forumdisplay.php?f=180)

---

