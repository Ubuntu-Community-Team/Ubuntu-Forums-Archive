---
title: "Server testing conundrum"
date: 2007-07-29
forum: Server Platforms
---

### Post by freebeer on 2007-07-29
Hiya folks.

Probably a dumb question, but here goes:

I have a test server running Apache2, an ftp server and a few other things on a LAN behind a router.  I have a dynamic DNS through DynDNS.  From outside the network, I (or anyone else) can access the server service by using the URL *sitename.org*.  So far so good.  Internally (from within the LAN) I can access/test the server services via direct (internal) IP address (ie 192.168.x.x/index.html).  So far so good in that respect.  However, I can't access the services internally by using the URL *sitename.org*.  I'm at a point where I need to be able to do so so that I can test/verify some things that need the actual URL.  For instance, I'm testing an html form that when you hit the submit button, it tries to send it to *[www.sitename.org](www.sitename.org)*, which, or course, doesn't work.  It would work if it tried to send it to 192.168.x.x, but then that wouldn't be valid for anyone outside the LAN.  Is there a way to achieve this?

I suppose I could use a dial-up connection, and come in that way, but I was hoping that there's a better and more elegant way to achieve this.

---

### Post by Mr. C. on 2007-07-29
This is a question that appears often in the forums.

Unless your router supports NAT loopback, you cannot use your WAN IP address from the LAN.  Your A record for your server is a public WAN IP address, and this of course is the IP your browser ultimately uses to connect.

The easiest solution is to simply add your hostnames to /etc/hosts, one for each site name you use.  More useful to a LAN with more hosts it to setup an internal (split) DNS server that resolves A records internally to LAN addresses.  Outsides will use public DNS servers, while your LAN clients use your internal DNS server.

MrC

---

### Post by freebeer on 2007-07-29
> **Mr. C. said:**
> This is a question that appears often in the forums. 

really?  I did a search, but must have used an innapropriate search string.  I wasn't really sure what to search for.  :redface:

> 
Unless your router supports NAT loopback, you cannot use your WAN IP address from the LAN.  Your A record for your server is a public WAN IP address, and this of course is the IP your browser ultimately uses to connect.


Cool.  "NAT loopback" is a term to remember.  Thanks.  My router doesn't appear to support such a thing - no surprise there... it's an el cheapo model.

> 
The easiest solution is to simply add your hostnames to /etc/hosts, one for each site name you use.  More useful to a LAN with more hosts it to setup an internal (split) DNS server that resolves A records internally to LAN addresses.  Outsides will use public DNS servers, while your LAN clients use your internal DNS server.

MrC

I like easy solutions.  :)  The server is running Dapper and the machine I'm testing the pages from is a Windows box.  So presumably it's the Windows box that I must make the hostname changes in.  Thanks for the help!

The split DNS server is an interesting concept.  I'll have to investigate that a bit further as I progress along the learning curve.  You've given me insight for my next project.  yay!  :smile:

---

### Post by Mr. C. on 2007-07-29
In Windows, the file is :

```
c:\windows\system32\drivers\etc\hosts
```

MrC

---

### Post by freebeer on 2007-07-29
Yep... found it easily enough.  Thanks again for your help... the hosts file did the trick!

---

