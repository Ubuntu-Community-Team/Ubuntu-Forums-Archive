---
title: "Soft Lockups on Gazelle V3"
date: 2007-10-20
forum: System76 Support
---

### Post by AusIV4 on 2007-10-20
My Gazelle V3 was left unbootable by the System76 driver launched right after gutsy, which lead to an updated driver a few hours later.

But right now, I can't tell that the driver does anything. I'm still getting soft lockups for about 30 seconds every once in a while, and my drive is /dev/sda (instead of /dev/hda). Any sign of a fix coming soon?

[EDIT]
Launchpad: [https://bugs.launchpad.net/bugs/155128](https://bugs.launchpad.net/bugs/155128)

---

### Post by thomasaaron on 2007-10-22
Yes. Here is the fix.

[https://bugs.launchpad.net/system76/+bug/117441](https://bugs.launchpad.net/system76/+bug/117441)

I realize it says it was for the Darter, but it was later applied successfully to the gazelle value.

In the meantime, take the cd or dvd that you are not using out of your drive and run your system 76 driver.

---

### Post by AusIV4 on 2007-10-22
The bug you referred to is about problems with the CD / DVD drive. While I've experienced those problems as well, the current problem occurs on Gutsy regardless of whether or not there is a CD in the drive.

---

### Post by thomasaaron on 2007-10-22
Did you ever do the firmware upgrade?
If you did not, the problem is probably still there. The System 76 driver never fixed it, it just provided temporary relief until we figured out the real fix.

It may just be manifesting itself slightly differently under Gutsy. 

If you've previously done the firmware upgrade, we should look elsewhere. If you have not, it needs to be done anyway -- and may solve the problem.

---

### Post by AusIV4 on 2007-10-22
Ran the firmware upgrade and it all seems back in order.

---

