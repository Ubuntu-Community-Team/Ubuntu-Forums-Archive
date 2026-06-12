---
title: "Shorewall is posting messages to the screen and the log files"
date: 2008-08-15
forum: Security
---

### Post by chrislynch8 on 2008-08-15
HI,

Shorewall is posting messages about dropping incoming packets to the screen. This should be happening it should only post to the log files.

Is there a setting somewhere that is telling shorewall to post messages to the screen. I can't type my commands as every few seconds the screen is refreshed.

rgds
chris

---

### Post by adieb on 2008-08-16
you could start shorewall telling it to write to /dev/null

command > /dev/null

---

### Post by chrislynch8 on 2008-08-18
Hi,

I've looked into this more and it is not Shorewall after all. All messages in the log file from the kernal are printing to the screen.

Any ideas why, this only started to happen recently. No new update etc. put in.

Rgds
Chris

---

