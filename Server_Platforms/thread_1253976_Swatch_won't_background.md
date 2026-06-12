---
title: "Swatch won't background"
date: 2009-08-30
forum: Server Platforms
---

### Post by vortmax on 2009-08-30
I'm using swatch to monitor my dhcpd logs and record an entry in a mysql database every time a new lease is created.  I have it working perfectly when running in the console (stdout dumped to the screen), but I cannot get this thing to daemonize.

When I try to background it with a &, it will run until the shell encounters a return.  I can background the process with either a & at run time or by ctrl-z (and bg), and it will run until I hit return and bring up a new line on the shell.  As soon as I do that, I get the [stopped] line, as if I halted the process but didn't background it.

I've tried using the --daemon flag as well, but that still dumps everything to stdout, and if you try and redirect with with &>, it just screws up the terminal until the process is halted.

Does anyone have experience making swatch work as a daemon, or can someone recommend something that works?  All it needs to do is watch a log file and fire off the line to a php script whenever it matches a simple regex.

---

