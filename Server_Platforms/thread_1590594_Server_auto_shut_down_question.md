---
title: "Server auto shut down question"
date: 2010-10-08
forum: Server Platforms
---

### Post by johan.alfa on 2010-10-08
Hello,

Our server ubuntu 10.04 did shut down yesterday afternoon.
I have no idea why it happened.
I'm not a real newbie but now I don't have a clue.
Where can I find in the log files what happened?

Thanks,

---

### Post by HermanAB on 2010-10-08
Howdy,

Is your server on a UPS?  If not, do yourself a favour and get one.

The /var/log/messages file may hold some clues.

---

### Post by johan.alfa on 2010-10-09
Hello,

Problem solved.
There was a power shut down problem in the office.

Regards,

Johan

---

### Post by CharlesA on 2010-10-09
Glad you got it sorted.

If you want to have the machine shutdown safely after a power failure, get a UPS that hooks up to the machine.

Personally I use APC UPSes, but that's probably due to brand recongnition and the fact that I haven't had any problems with them. Also being able to use apcupsd is a nice thing too. :)

---

