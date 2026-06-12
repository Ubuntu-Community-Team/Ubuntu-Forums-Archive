---
title: "SSHD - Temp files"
date: 2008-07-14
forum: Security
---

### Post by Spitphire on 2008-07-14
Hello,

I've searched, but have yet to find an answer.  I have sshd running with tunneling enabled.  When a user creates a connection and requests data through the tunnel from say a website (i.e. socks via Firefox); does the server store the files that it downloads from the website in any particular temp file location before forwarding it to the user?  

I would like to know where this information is saved prior to it being forwarded to the user so I can setup some type of deletion/wipe method so that their (the user) security integrity stays intact.  Any info on this subject would be much appreciated.

Thank you,
spit

---

### Post by Spitphire on 2008-08-03
*Bump*

---

### Post by daleus on 2008-08-03
If by tunelling you mean something like

-D 7070 and then using the internet via that, then NOTHING is kept.


However if you're using squid, you'll have to clean up squid's files.


If you don't know what squid is, you probably aren't using it.

---

