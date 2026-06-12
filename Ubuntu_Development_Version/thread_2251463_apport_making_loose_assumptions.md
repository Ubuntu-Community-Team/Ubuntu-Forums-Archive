---
title: "apport making loose assumptions"
date: 2014-11-04
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-11-04
Apport once again is assuming incorrectly.

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1389286](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1389286)

---

### Post by mc4man on 2014-11-05
Could be if you assume that you means you.
Likely just a point in time message of no concern?

---

### Post by grahammechanical on 2014-11-05
@ventrical

If it wasn't you that modified that file. Then it must have been HAL 2000. If you next get a warning that the WiFi adapter is about to breakdown. Then whatever you do, don't go out the airlock. :)

Or perhaps Apport is having difficulty with the change over from Upstart to SystemD.

Regards.

---

### Post by ventrical on 2014-11-05
> **mc4man said:**
> Could be if you assume that you means you.
Likely just a point in time message of no concern?

Niether language nor logic is a pre -supposition for mathematics. (Kurt jan Von Brower)

Yes. Correct. basically the bug is a 'language' bug.  The message flag should be more declarative. "It seems"  is vague.
"It seems you" is not a valid argument. So apport is using expert algorithms,  but this type of randomness can send one on a wild goose chase.

---

### Post by ventrical on 2014-11-05
> **grahammechanical said:**
> @ventrical

If it wasn't you that modified that file. Then it must have been HAL 2000. If you next get a warning that the WiFi adapter is about to breakdown. Then whatever you do, don't go out the airlock. :)

Or perhaps Apport is having difficulty with the change over from Upstart to SystemD.

Regards.

:)

  My apologies. The bug is more or less a frivolous 'language bug'  which  makes an erroneous declaration, probably harmless, but promotes possible downtime.

  The flag should read; "The file at /ext/apt/ whichever/whatever.file has been overwritten because you were wearing mittens while your cat was having kittens ! :)

lol

---

### Post by Bucky Ball on 2014-11-05
Known issue. Apport used for debugging development releases and hasn't been switched off. 99% of the time there is nothing wrong. To switch it off:

[http://linuxg.net/how-to-disable-the-apport-error-reporting-on-ubuntu-14-04-trusty-tahr/](http://linuxg.net/how-to-disable-the-apport-error-reporting-on-ubuntu-14-04-trusty-tahr/)

Reboot.

---

### Post by Bucky Ball on 2014-11-05
Generally is. If you get the report as soon as you get to a desktop after boot, known issue. Apport used for debugging development releases and hasn't been switched off. 99% of the time there is nothing wrong. To switch it off:

[http://linuxg.net/how-to-disable-the-apport-error-reporting-on-ubuntu-14-04-trusty-tahr/](http://linuxg.net/how-to-disable-the-apport-error-reporting-on-ubuntu-14-04-trusty-tahr/)

Reboot.

---

### Post by zika on 2014-11-06
Before turning it off (I do turn it off by default usually) try to clean /var/crash in order to not get bothered with apport because of (even) one crash that You did not report months ago. ;)

---

### Post by ventrical on 2014-11-06
Thanks you both.

Regards..

---

