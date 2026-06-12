---
title: "FreeRadius Cleartext-Password?"
date: 2011-04-07
forum: Server Platforms
---

### Post by RadiusD on 2011-04-07
Hello,

I setup a freeradius server that is doing mac authentication and is using a mysql database to store macs. 

When a user tries to authenticate the server reads his mac as a "User Password =" how do I make it read as a "clear-text password :=" what setting do I need to change for the server to interpret the password as cleartext.

---

### Post by HermanAB on 2011-04-08
Howdy,

For RADIUS, a Red Hat distro would be the one to use if you want some support from the community.  On Ubuntu, I would be amazed if there is one other person who uses RADIUS.

As far as I can remember, in this howto, I used clear text passwords:
[http://www.aeronetworks.ca/howtos/radius.html](http://www.aeronetworks.ca/howtos/radius.html)

---

