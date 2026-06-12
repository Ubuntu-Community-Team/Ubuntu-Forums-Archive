---
title: "simple radius server with gui"
date: 2007-09-13
forum: Server Platforms
---

### Post by inphektion on 2007-09-13
Is there a recommended radius server to use for simple wireless mac address filtering?  I just want to point my access point at a radius server over port 1812 and have it check a list there for a valid mac address or not.  Ideally I'd like to be able to enter the mac's via a web gui. 
Anything I tried seemed really complex, any suggestions or tutorials?

---

### Post by a9k on 2007-09-14
If you are dealing with a small number of MAC's (like <=253), you could skip radius completely and use DHCP fixed MAC-ip allocations while not letting DHCP handout any ip's that aren't fixed. Most home router boxes allow this.

If you are managing a campus with 1000's of kids using the wifi then you have a much tougher problem. Radius normal usage is for authenticating a user with username and password. For WIFI usage you'd be using 802.1X.
There is an open source project for 802.X1
[http://open1x.sourceforge.net/](http://open1x.sourceforge.net/)

---

