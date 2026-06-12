---
title: "I cannot connect apache from my external ip"
date: 2008-07-24
forum: Server Platforms
---

### Post by samkon on 2008-07-24
as the topic which's link is below;
[http://ubuntuforums.org/showthread.php?t=627293&page=2](http://ubuntuforums.org/showthread.php?t=627293&page=2)

I cannot connect apache server with my external IP address.

I added these to ports.conf
```
Listen 8080
```

and I also routed my 8080 port to my local IP.

But I still cannot connect to server by using this query;
hxxp://[ext_IP]:8080

But on port 80 my Airties modem works correctly..

what can do?

thanks..

---

### Post by freebeer on 2008-07-24
I'm missing a couple of pieces of information.  Ok, so you forwarded the port 8080 from your router to the internal IP address of the server on your LAN, right?

ok... now did your really type "h**xx**p://" or was that a typo and you really meant "h**tt**p://"?

Assuming it was a typo, from **where** were you typing this address?  From the web server or another machine on the LAN?  If so, that is not surprising that you couldn't get a connection.  Most routers cannot route an internal request to the external address that is actually on your internal network.  If you follow me. :D  You may very well find that if you typed that from a machine external to your LAN, you would get the appropriate response.  From within the LAN, you either need to use the internal address, or set an alias up in your /etc/hosts file (on the machine making the enquiry) to direct the request to the right address.

That may be a little confusing.  If you can tell me from where you're making these requests, I can be a little more specific.

---

### Post by samkon on 2008-07-25
first, as you hope I gave "hxxp://.." as an example for well reading. :)

I did not changed anything yet about the configurations those I did. So I will try to connect my pc out of the LAN..

thank you for giving a try to me..

---

