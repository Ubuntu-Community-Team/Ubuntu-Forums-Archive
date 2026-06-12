---
title: "apt-get port"
date: 2006-11-12
forum: Server Platforms
---

### Post by brakmaren on 2006-11-12
Hi
Just reinstalling everything again :) 
Got a box with ipcop, and that installation went greate.
Now when i'm reinstalling my LAMP (6.10) i ofcource can't apt-get update before opening ports.
So the question.
What port does ubuntu use for update ?
Thank's

---

### Post by mark_g on 2006-11-12
I think it just uses http to transfer the files. So it'll connect on port 80 of the update server to a random high port number on your pc, just like your browser does.
So if you can surf the web, you should be able to also dowload upgrades. If you do have problems, check the proxy server settings in the apt-get configuration file.

---

### Post by brakmaren on 2006-11-12
Nope, it's locked down. Traffic out is open but traffic in is closed in default state. Tried opening 80 in to no avail. Any more tipps?

---

### Post by brakmaren on 2006-11-12
Tried opening ALL ports. STILL no contact ???
I can ping from green to orange, but not orange to red or orange to green.

---

### Post by druhboruch on 2006-11-12
I run standard green/red IPCop 1.4.11 installation and everything is OK.

You shouldn't have to open any ports for apt to work.

---

### Post by brakmaren on 2006-11-12
Sorry. I re-started ubuntu LAMP install, and now everything works fine ??
Sorry for wasting space :oops:

---

### Post by brakmaren on 2006-11-13
Well it turned out it whas not me thst whas broken :) 
It whas intermitent fault in one of the net cables.
Now cable is exchanged and everything runns smooth. :-D

---

