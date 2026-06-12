---
title: "Port knocking (client side question)"
date: 2009-12-09
forum: Security
---

### Post by Jive Turkey on 2009-12-09
I've been curious about port knocking for extra security on an internet facing server I have.  I've looked at the docs for the package knockd and it looks pretty straightforward to configure but I'm not clear on how to send the knocks from the client to open up the port(s).

Also, I could need to access the server from a windows or mac client if anyone is familiar with packet knocking on those OS's.

Also, would knockd conflict with ufw?

---

### Post by Dr Small on 2009-12-10
> **Jive Turkey said:**
> I've been curious about port knocking for extra security on an internet facing server I have.  I've looked at the docs for the package knockd and it looks pretty straightforward to configure but I'm not clear on how to send the knocks from the client to open up the port(s).

Also, I could need to access the server from a windows or mac client if anyone is familiar with packet knocking on those OS's.

Also, would knockd conflict with ufw?
I understand that this does not directly answer your question, but it is something worth mentioning, regardless. Nearly two years ago (oh my! Has it really been that long?!) Kevdog wrote an article on setting up fwknop, which is a portknocker, in his step by step guide, and it really was a handy little thing. You can find his tutorial here, if you are interested in it: [http://ubuntuforums.org/showthread.php?t=812573](http://ubuntuforums.org/showthread.php?t=812573)

Best Regards,
Dr Small

---

### Post by Jive Turkey on 2009-12-11
Thanks for the reply, I'll look into that.  My main concern is whether it is possible to knock the ports without a special platform-dependent client.

---

### Post by BkkBonanza on 2009-12-12
This may also not be exactly what you want but I think it has a Python client that should be useable on most systems. The main reason I give this link is that I think he has some important ideas that need reading if you are setting up port knocking and I always think of it when someone talk about setting it up. If you do it wrong then you're just making things worse... and also Moxie has lots of nifty stuff to read and understand.

[http://www.thoughtcrime.org/software/knockknock/](http://www.thoughtcrime.org/software/knockknock/)

---

### Post by kevdog on 2009-12-12
Port Knocking is useful particularly if you have something to protect.  There are various port knocking implementations -- each vary dependent on the security offered by the scheme.  fwknopd is one implementation I am aware of that offers increased security because the knock sequences are non-replayable, encrypted, and time dependent.  These are important only if you feel the need to protect the knock sequence from sniffers or third parties which may intercept the knock packet and use the provided information for their own nefarious purposes.  

Here is a short video where the creator of fwknop discusses his implementation.  The first 20 min of the video discusses fundamental concepts in port knocking so it gives you a pretty good background whereby you can go evaulate other port knocking schemes and pick the implementation suitable for you:
[http://www.ustream.tv/recorded/2505225](http://www.ustream.tv/recorded/2505225)

Here is the master list of port knocking schemes that I now of:
[http://www.portknocking.org/view/implementations](http://www.portknocking.org/view/implementations)
I haven't tried them all out.

---

