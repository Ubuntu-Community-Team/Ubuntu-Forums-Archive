---
title: "Lost Root Password!!! Please help"
date: 2012-07-16
forum: Server Platforms
---

### Post by pstonge on 2012-07-16
Hey everyone, I am here because my boss at work gave me the permission to service our helpdesk webserver which runs ubuntu 9.04 server. 
 
But the thing is, he gave the permission to a former employee, and this guy changed the passwords for root. And now we cannot login. 
 
Is there anything we can do about this..please let me know.

---

### Post by drmrgd on 2012-07-16
Have a look at the Community Documentation for this:

[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

It'll just be a matter of booting to a recovery console and resetting the password from there.  Hopefully that helps!

---

### Post by Cheesemill on 2012-07-16
This link describes the process as well:

[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by Cheesemill on 2012-07-16
Also I would think about upgrading the Server.

9.04 reached end of life over 18 months ago and as such is no longer supported and no longer receives any security updates. There could very well be security flaws that could allow anyone to gain root access to the server.

---

### Post by pstonge on 2012-07-16
Thanks everyone, I am going to do some digging around and see if i can go ahead with the upgrade, but my boss was wanting to take the server off of ubuntu and make it windows (gross) lol, so maybe i can talk him into keeping it, and just maybe if i learn ubuntu enough i can convince him to change our other servers to ubuntu. 
 
Thanks guys again for your help!!!

---

### Post by CharlesA on 2012-07-17
Ehhh, I have a wiki server at work running off a VM and it is terribly slow (tho I am not sure if it is cuz it is a VM or if it is cuz it is running Windows).

Upgrading from 9.04 is going to be a chore, but once you get it to 10.04, you should be able to bump it to up to 12.04 with little difficulty.

See here:
[https://help.ubuntu.com/community/EOLUpgrades/](https://help.ubuntu.com/community/EOLUpgrades/)

---

### Post by LHammonds on 2012-07-18
Rather than performing experimental upgrades, you might want to try setting up a virtual Ubuntu 12.04 server and see if you can transfer the data from 9 to 12.
 
LHammonds

---

### Post by CharlesA on 2012-07-18
> **LHammonds said:**
> Rather than performing experimental upgrades, you might want to try setting up a virtual Ubuntu 12.04 server and see if you can transfer the data from 9 to 12.
 
LHammonds
Agreed.

---

