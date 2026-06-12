---
title: "Restart a service peridoically?"
date: 2009-08-31
forum: Server Platforms
---

### Post by afowler on 2009-08-31
Hello,

I am writing an application to run an Ubuntu server that needs to run every few seconds.

For now, I am writing it in python in a loop that sleeps for a few seconds and runs again.  (Would be launched automatically at start up, i guess.)


However:

1) I do not trust that my code will not crash.
2) I do not trust my code to run forever with out a memory leak.

So I am looking for a way to solve both problems.

(I thought about just using cron to run a fresh copy of my program, but I need it to run more than once a minute.)


Any ideas?

Thank you,
:)

---

### Post by hessiess on 2009-08-31
rely on the internal loop mostly, have a chron job start the program periodcally have the program check if it is already running at start-up and quit if it is.

A python program shouldn't leek memory, its garbage collected.

---

