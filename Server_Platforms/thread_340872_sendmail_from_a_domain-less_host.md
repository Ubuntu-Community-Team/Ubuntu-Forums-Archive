---
title: "sendmail from a domain-less host"
date: 2007-01-17
forum: Server Platforms
---

### Post by brettfavre on 2007-01-17
I'm running a development server on a home connection (charter cable service).  I have sendmail installed and tested it using php's mail() function, however none of the emails are being received by the recipient. I checked the sendmail log and see that the connection to recipients mail server is timing out.  Anyone have any ideas why this is happening, and how to fix it?

---

### Post by jtc on 2007-01-18
Do you know if your ISP is blocking your outbound port 25? Nowdays it's quite common.

Iif that's the case, you'll nead to tell sendmail to use a relayhost.

---

### Post by jactheman on 2007-01-27
hello Did you figure out how to work sendmail I am also having the same issue over my ISP..

Please let me know how you did it. 
Thanks

---

