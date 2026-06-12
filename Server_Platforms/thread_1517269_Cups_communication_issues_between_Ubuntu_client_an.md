---
title: "Cups: communication issues between Ubuntu client and server"
date: 2010-06-24
forum: Server Platforms
---

### Post by mrmooge88 on 2010-06-24
Ubuntu 10.04 Server, 32bit, HP Deskjet D4160
Ubuntu 10.04 Desktop, 64bit

The printer works okay when plugged in through USB on my laptop. It is currently set up as a network printer through CUPS and Samba on the server.

When the printer is plugged into the server I can issue the following command when SSH'd in "lp text-file.txt" and print the document just fine. But if I try from my desktop to print through the network it only works about 20% of the time from both the Samba and the CUPS protocol.

I can see the document in the top right indicator applet showing that the document is waiting to be printed.
Running "sudo /etc/init.d/cups status" on both computers shows that cupsd is running.

I didn't install cups when I did the initial install of the server.

When I configured the printer I used the CUPS web user interface.

A friend tried to print with his Window 7 laptop to Samba but he didn't have any luck either.

Any ideas?

---

