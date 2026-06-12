---
title: "Rsync bus error issue"
date: 2011-08-01
forum: Server Platforms
---

### Post by _Doc_ on 2011-08-01
I am currently trying to move data off of our Windows 2000 server machine onto Ubuntu 10.04 server box.  I initially tried using DeltaCopy/Rsync on Windows to move the data to the Ubuntu server.  It would run for about an hour or 2 and then the Ubuntu server would fold, the storage location would become unresponsive and the whole system would stop working properly.  I would get IO errors across the console window.  So I thought maybe it was Windows causing the problem so I moved storage into the Ubuntu server and did Rsync and got the same results.  I ran it from the command line and got an error of Bus error.  Not much to go on and maybe I can get some help with hunting down what is causing the issue.

The servers are HP G3 ML370... old servers but they still run :)
Both have raid systems using 3ware 9550SX cards.  The old Windows system has 3, 1 Terabyte drives and the new Ubuntu 10.04 system has 3, 2 Terabyte drives.  They are P4 Xeon servers so only using i386 version of Ubuntu.  The Rysnc always works for a while but tanks after a couple of hours... using cp to copy the information doesn't seem to cause any problems as I ran this for a day or so and didn't have any issues.

---

