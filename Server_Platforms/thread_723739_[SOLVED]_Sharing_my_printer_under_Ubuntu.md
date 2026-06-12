---
title: "[SOLVED] Sharing my printer under Ubuntu"
date: 2008-03-13
forum: Server Platforms
---

### Post by cpbl on 2008-03-13
Hi. I have an Ubuntu Gutsy laptop with an HP laser printer attached via USB.
It works nicely, set up with the default driver and configuration given by the desktop printing dialogue.
I want to share it with my officemate running a Mac.
I used the printing control dialogue to turn on sharing for the printer.

The Mac sees the printer, reports its status, etc. The Mac prints a file to it.
The print job ends up in the queue that is visible through "lpq" but not anywhere else (in the CUPS queue??).  The printer does not print it. It just sits "ready", ignoring the job.

Does anyone have an idea what am I doing wrong? 
For a moment, I thought everything was going to work brilliantly on the first go...

thanks,
c

---

### Post by HermanAB on 2008-03-13
Use the web interface to CUPS and see whether the printer is in fact shared and online.  You probably have multiple installations of the printer and the one the Mac sees is the dud one:

[http://localhost:631](http://localhost:631)
First click the Administration tab and log in as root, after that the rest of the wizard should work

Cheers,

Herman

---

### Post by Harlequin on 2008-03-14
You will probably also have to change cups.conf from listen on Localhost:port to listen on *:port

This will open the printer port to external connections.

---

### Post by cpbl on 2008-03-20
The problem was that there were for some reason two versions of the printer set up by Ubuntu.  I just had to delete one of them, and then jobs coming from the Mac actually ended up on paper.

Thanks!
c

---

