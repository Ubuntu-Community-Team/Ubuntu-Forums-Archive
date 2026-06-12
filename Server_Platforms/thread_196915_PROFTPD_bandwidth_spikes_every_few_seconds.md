---
title: "PROFTPD bandwidth spikes every few seconds"
date: 2006-06-14
forum: Server Platforms
---

### Post by gavagai on 2006-06-14
I cannot figure out how to prevent proftpd from killing my network performance.

I have successfully set the 'transferrate' directive.  It has some effect, and from the client side seems to set an absolute cap, but if I monitor my connection I can see that every few seconds the server completely maxes out my bandwidth.

I have successfully setup wondershaper.  Same exact problem.

How can I fix this?  Network performance is atrocious when someone is accessing my FTP server.

EDIT:  I have confirmed the same behavior with pure-ftpd.

---

### Post by nkassi on 2006-06-15
It probably won't fix your problem you might want to take a look at vsftpd. I have had lots of success with this ftp server. Plus it's very lightweight and secure.

Nic

---

### Post by gavagai on 2006-06-15
Well, I made some progress.  By pushing my upload bandwidth down to 150kbps with wondershaper, I made some improvement.  I can't get rid of the spiking, but now the spiking doesn't quite max out my whole bandwidth.

It would be nice if I could determine a steady bandwidth (right now the system is sort of inefficient and wasteful) but at least this seems to be better for my overall network performance.

---

