---
title: "Samba &amp; wan"
date: 2008-12-27
forum: Server Platforms
---

### Post by Henry80 on 2008-12-27
Hi guys, i'm not an linux expert but i know somethings already but, since few days ago, i'm trying to set up a samba server with  wan connection(also if i know that it is very unadvisable do it). Until now, i've opened the UDP-TCP on my router throught virtualserver-nat configuration, so that all incoming traffic on those ports go to my samba machine. Unfortunately i still cant have access from internet to my samba machine.
ANy help guys?
Thank you very much.
Henry

---

### Post by hictio on 2008-12-27
What type of internet connection do you have?
I'm not 100% sure, but its pretty damn sure your ISP block those ports -I mean the Windows sharing ones- like Fort Knox, its a hell of a easy way of distribute virus.

---

### Post by Henry80 on 2008-12-28
mmm...it sound a bit strange for me ..
instead, any advice about samba configuration?? maybe there i have done something wrong.
ANyway .Thank you .

---

### Post by HermanAB on 2008-12-28
Don't use Samba over the public internet.  Your machine will die a horrible death pretty soon if you do.   Most routers nowadays block the Samba ports 135-139 and 445 by default.

You could run Samba over SSH, which would encrypt it:
[http://aeronetworks.ca/samba-ssh-tunnel-howto.htm](http://aeronetworks.ca/samba-ssh-tunnel-howto.htm)

Cheers,

Herman

---

### Post by cariboo on 2008-12-28
I would suggest using [canyouseeme]("http://www.canyouseeme.org/") to see if your ISP is blocking any ports.

Jim

---

### Post by Henry80 on 2008-12-29
THank you for the replies guys. ok, i think my ip is blocking those ports.
So, how could i change listening ports on samba??
Thank you. 
henry

---

