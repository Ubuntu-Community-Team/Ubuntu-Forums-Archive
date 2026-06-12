---
title: "error in Ubuntu 12.04"
date: 2012-04-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by wpshooter on 2012-04-23
I installed 12.04 daily build on my test machine several days ago and I kept getting an error message regarding Precise 12.04 had detected some type of error and asked if I wanted to report it, which I did.

I would like to give the install another try IF this has been fixed.

Does anyone know if this problem has been fixed ???

I still have the last install on the test machine, so if more details as to the exact nature of the error are needed, I can probably provide them.

Thanks.

---

### Post by Mathor on 2012-04-23
> **wpshooter said:**
> I installed 12.04 daily build on my test machine several days ago and I kept getting an error message regarding Precise 12.04 had detected some type of error and asked if I wanted to report it, which I did.

I would like to give the install another try IF this has been fixed.

Does anyone know if this problem has been fixed ???

I still have the last install on the test machine, so if more details as to the exact nature of the error are needed, I can probably provide them.

Thanks.

I haven't had this problem in about a week or so. I would suggest grabbing the newest daily build. I'm almost certain the newest iso is the final release of 12.04

---

### Post by xebian on 2012-04-23
> **wpshooter said:**
> I installed 12.04 daily build on my test machine several days ago and I kept getting an error message regarding Precise 12.04 had detected some type of error and asked if I wanted to report it, which I did.

I would like to give the install another try IF this has been fixed.

Does anyone know if this problem has been fixed ???

I still have the last install on the test machine, so if more details as to the exact nature of the error are needed, I can probably provide them.

Thanks.

My wild guess is it has been fixed.):P

---

### Post by grahammechanical on 2012-04-23
If you reported it on Launchpad then you will have the bug number and you can use that to find the Launchpad reference to the bug to see what has been done about it. You would also have received 2 emails about your bug report from Launchpad.

It all depends how serious the bug has been rated and that depends on how many people are affected by it and whether the developer has been able to fix what is wrong and get his fix into the OS.

Regards.

---

### Post by wpshooter on 2012-04-23
> **Mathor said:**
> I haven't had this problem in about a week or so. I would suggest grabbing the newest daily build. I'm almost certain the newest iso is the final release of 12.04

I just went to update manager & installed all of the available updates (49, I think) and then did the restart when prompted.

However as soon as I got back up to the desktop the same report of system error popped up again after about 2 minutes.

However, I went back into update manager again and checked off the proposed updates parameter, did a poll for more updates, but there were none.  I then did a second restart and this time when I got back to the desktop the system error did NOT pop up.  How do you explain that or do you just say thank the Lord and move on ????

Thanks.

---

### Post by mc4man on 2012-04-23
On newish installs during dev before apport is shut off/throttled down (whatever), you can see the same 'bug' causing a pop up. Most times it's of little concern

Often it's caused by this bug which refuses to die
[https://bugs.launchpad.net/ubuntu/lucid/+source/libx11/+bug/507062](https://bugs.launchpad.net/ubuntu/lucid/+source/libx11/+bug/507062)

---

