---
title: "Port Forwarding not working"
date: 2009-12-03
forum: Server Platforms
---

### Post by erroldennis on 2009-12-03
i installed a ubbuntu 9.10 server and installed Firestarter to forward web & mysql server to another internal LAMP server.  I can connect from the internal network but not from the web.   CAN ANY ONE HELP.  Take time with me please i new to UBUNTU server & port forwarding.

Please note that the ports are not closed as I test the port from [http://www.canyouseeme.org/]("http://www.canyouseeme.org/") and the report was fine for both ports 80 and 3306. 
  
I urgently need help.

---

### Post by cdenley on 2009-12-03
So you have a router port forwarding to server A, then firestarter is configured to forward those ports to server B? I didn't even know firestarter can do that. Why not configure your router to forward directly to server B? You can try using rinetd instead.

---

### Post by erroldennis on 2009-12-03
Thanks for the quick reply.  what is rinetd and how do i use it?

---

### Post by cdenley on 2009-12-03
> **erroldennis said:**
> Thanks for the quick reply.  what is rinetd and how do i use it?

First, clarify what you're trying to do exactly.

---

### Post by cdenley on 2009-12-03
I should probably point out that not all routers will follow port forwarding rules for requests received on a LAN port destined for a WAN IP. In other words, some routers won't allow you to access your servers with a WAN IP even though it works correctly outside your network. It might help if you post your IP address so we can test it ourselves.
[http://whatismyip.org/](http://whatismyip.org/)
It sounds like canyouseeme.org is establishing a connection, so perhaps it is working already.

---

### Post by erroldennis on 2009-12-03
i am trying to do port forwarding.  ie: redirect traffic from my global ip 208.... to my web and mysql server on a local machine 10.0.0.211.

rinetd seems to be exactly what I need andd it seems simple enough to use.

 i installed rinetd, made the changes in the /etc/rinetd.conf file but how do i restart the service/

---

### Post by cdenley on 2009-12-03
> **erroldennis said:**
> i am trying to do port forwarding.  ie: redirect traffic from my global ip 208.... to my web and mysql server on a local machine 10.0.0.211.

rinetd seems to be exactly what I need andd it seems simple enough to use.

 i installed rinetd, made the changes in the /etc/rinetd.conf file but how do i restart the service/

No, don't use rinetd. Your first post seemed to indicate your were port forwarding with firestarter, meaning you were redirecting from one server to another. Now, it sounds like you are simply port forwarding from the router to the server, as I had suggested, which does not require rinetd.

If you have port forwarding configured, and your servers are running, it may already be working. First, we need to establish that there is a problem. Are you sure the servers cannot be accessed over the internet from outside your network?

---

### Post by erroldennis on 2009-12-03
I successfully restarted using the comand:

/etc/init.d/rinetd restart


I still cant see my website when I type my global IP addrss.

---

### Post by cdenley on 2009-12-03
> **erroldennis said:**
> I successfully restarted using the comand:

/etc/init.d/rinetd restart


I still cant see my website when I type my global IP addrss.

Which as I explained earlier doesn't mean anything if you are doing this from the same LAN as the server! Stop using rinetd!

---

### Post by erroldennis on 2009-12-03
Please check for me:

[http://www.dentronix.com.jm]("http://www.dentronix.com.jm")

---

### Post by cdenley on 2009-12-03
Looks like it's working.
> 
Our site is temporarily down.


We are doing everything to get it back up in the shortest posibly time.


Sorry for the inconvenience.


DenTronix Ltd.


Are you sure you want webmin access available to the whole internet? I hope you use a strong password.

---

### Post by erroldennis on 2009-12-03
i got a friend to do the check from outside my network and just as you suggest its working fine.  

THANKS A MILLION.

---

### Post by erroldennis on 2009-12-03
THanks again.  i fixed the webmin access.

---

