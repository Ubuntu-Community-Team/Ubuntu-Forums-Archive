---
title: "CUPS Printer hangs after one job"
date: 2016-10-09
forum: Server Platforms
---

### Post by brownzeus on 2016-10-09
Hi all,
 In advance I'd like to apologize if this was the wrong forum  to post this issue to.

I am new to Linux, but have dedicated some time to set up a Common Unix Print Server at work, so we can keep track of pages printed per job so that we can charge accordingly (Its a Computer Cafe).
Out of the 3 printers, I've hooked up and installed 2, the third printer doesn't have any compatible Gutenberg drivers in existence, and the ppd doesn't appear to help anything, but I digress.

The two printers I do have installed are a HP Laserjet 4200dtn, that works as it should, with no issue, and the second is a Canon Pro9500 Mark II, which kind of works, but gives a pretty annoying bug.

The Canon printer only prints One job at a time before I have to restart my whole server. Here is exactly what happens:

-Send a print to the Canon Printer
-The Printer does print the job
-Then the printer is stuck at "Idle  - Sending Data to Printer"
-From terminal, I run "sudo service cups restart" to try and remedy the problem
- Cana still stuck at the same status

And then I'll reboot the whole server to get it going again because it won't print anything while it's in this status.

I tried searching through multiple forums to try and fix it but I couldn't find any solutions.

Anyone have any ideas?

I'm running Ubuntu Server 16.04 LTS, the printer is hooked up via usb to the server.

---

### Post by brownzeus on 2016-10-09
Update:

Don't know what changed exactly, but now when I send a second job after a successful one, the printer n the CUPS side will hand at "Processing - Sending data to printer", and on the printer itself the data light blinks as if it were getting info to print with, it was not doing this before.

---

