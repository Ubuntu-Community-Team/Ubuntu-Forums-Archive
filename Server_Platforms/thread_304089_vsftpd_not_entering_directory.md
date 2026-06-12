---
title: "vsftpd not entering directory"
date: 2006-11-21
forum: Server Platforms
---

### Post by jbtito03 on 2006-11-21
Hello...

I really have to fix my local ftp server and dunno how.

In my local network it works fine. When someone outside wants to access it he can log in but gets the error:

Error:	Transfer channel can't be opened. Reason: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.
Error:	[B][B]Could not retrieve directory listing

I opened up the listening ports in the cfg and in the firewall and also set the server into passive mode.

I am using a 6.06 LAMP server

What could be wrong?


Cheers 

JB

---

### Post by jbtito03 on 2006-11-23
Could please take someone a look at this?

Thx..

JB

---

### Post by MJN on 2006-11-23
Is the person outside connecting in passive mode?

Post your vsftpd config, and connection log (from the client if possible).

What setup have you got? Is there any NAT/router between you and the Internet?

Mathew

---

