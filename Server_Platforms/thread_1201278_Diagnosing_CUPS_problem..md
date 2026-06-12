---
title: "Diagnosing CUPS problem."
date: 2009-06-30
forum: Server Platforms
---

### Post by Lucky. on 2009-06-30
A couple of weeks ago I set up a print server with CUPS (Ubuntu 9.04).  It worked very well.

Then I moved said server and printer to a different room.  The printer still shows up on the network, but printing to it does nothing.

The two possible problems I can imagine are:

1.  Server was powered off without a proper shutdown (accident).
2.  Printer might not be plugged into the same USB port it was originally.

Any ideas on how to diagnose the problem?  Special commands or logs to check?  Everything appears just fine, but nothing prints, and I'm receiving no visible error messages.

---

### Post by LepeKaname on 2009-07-01
> "2. Printer might not be plugged into the same USB port it was originally." 

As far as I know it doesn't matter in Linux (just in Windows).

However, if you enter the cups control panel (localhost:631) and go to printer properties, it will display the USB port in a string. (I can't recall exactly as I don't have cups at this computer right now). Could this means that, for CUPS printers, the port is important? I'm not sure.

But if your feeling is correct and you don't remember in which port was connected, try to reinstall it (from CUPS control panel). It may take you like 5 minutes (I hope).

Good luck.

---

### Post by Lucky. on 2009-07-01
Thanks a bunch man.  I tried the web interface, and once again, everything appeared to work perfectly.  However the printer simply wouldn't print.

I connected the printer directly to my local machine, detected the drivers, and got everything set up.  Once again, no printing...

At this point, I tried a new USB cable.  All fixed, everything is good now.  Prints fine.

Wasn't a software problem after all.  Doh!

Thanks again!

---

