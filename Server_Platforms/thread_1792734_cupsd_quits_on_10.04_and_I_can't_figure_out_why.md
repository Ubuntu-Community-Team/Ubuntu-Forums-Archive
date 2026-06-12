---
title: "cupsd quits on 10.04 and I can't figure out why"
date: 2011-06-28
forum: Server Platforms
---

### Post by poltr1 on 2011-06-28
I have a client with a server running Lucid (10.04).  Several months ago, I installed cups 1.4.3 on this server.  There is an HP LaserJet 4050n connected to this server, via the parallel port.

I will frequently get calls from their office administrator saying he can't print to this printer.  I come in to the office, check to see that cupsd is running, and it isn't.  I then log in to the server, restart cups, and all is right with the world.....until I get the next call.

I looked at the server's log files in /var/log and can't see where or why cupsd is shutting down.  No one's bouncing the server.

I know that the printer is shut down at the end of the day to save energy.

As a temporary workaround, I put a line in the crontab file to restart cupsd at 8am every morning.

Any ideas as to how I can permanently fix this?

---

