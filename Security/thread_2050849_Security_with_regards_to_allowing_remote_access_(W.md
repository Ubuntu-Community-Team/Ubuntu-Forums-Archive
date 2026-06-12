---
title: "Security with regards to allowing remote access (WAN) to our internal Ulteo Server"
date: 2012-08-31
forum: Security
---

### Post by greavette on 2012-08-31
Hello,

We have as part of an internal application we use a feature that allows clients to download results through their browser (serves up a webpage).  Ulteo has a lot of benefits to our internal workers for serving up applications so my idea is to create user id's for internal users and external clients, add a link on our external webpage that would connect to our Ulteo Server (use port forwarding in our Security Router) so clients could login and have presented to them a link to the webpage where they can download results of the work we have completed for them.  The beauty of this is that by serving up Ulteo this way we not only have remote access for our clients, but we can now have some internal workers at our company use this link to access internal apps when needed.  

Am I opening up a security hole here?  I've thought of using an SSL-VPN clientless connection but it's not really clientless since it downloads and installs a java agent on-the-fly to allow the connection to the internal server that serves up what we want external people to see.   Or to be safe, should I put this Ulteo Server in our DMZ instead? I would install Ulteo on Ubuntu Server so should I put this server in my DMZ and create a webpage link to our internal webpage?

Thoughts?

---

### Post by dcstar on 2012-09-01
> **greavette said:**
> Hello,

We have as part of an internal application we use a feature that allows clients to download results through their browser (serves up a webpage).  Ulteo has a lot of benefits to our internal workers for serving up applications so my idea is to create user id's for internal users and external clients, add a link on our external webpage that would connect to our Ulteo Server (use port forwarding in our Security Router) so clients could login and have presented to them a link to the webpage where they can download results of the work we have completed for them.  The beauty of this is that by serving up Ulteo this way we not only have remote access for our clients, but we can now have some internal workers at our company use this link to access internal apps when needed.  

Am I opening up a security hole here?  I've thought of using an SSL-VPN clientless connection but it's not really clientless since it downloads and installs a java agent on-the-fly to allow the connection to the internal server that serves up what we want external people to see.   Or to be safe, should I put this Ulteo Server in our DMZ instead? I would install Ulteo on Ubuntu Server so should I put this server in my DMZ and create a webpage link to our internal webpage?

Thoughts?

Not an Ubuntu Support issue, this forum is "General Help" for using Ubuntu, not "General Help" for whatever else is in the universe. Try:

[http://www.ulteo.com/home/en/forums](http://www.ulteo.com/home/en/forums)

---

### Post by greavette on 2012-09-04
Fair enough.  Just thought I'd try it my question here, but I understand it's not an Ubuntu question.

Thank you.

---

