---
title: "Multiple external ip's - how to? TOR"
date: 2007-09-01
forum: Server Platforms
---

### Post by kudeta on 2007-09-01
So i bought myself a remote server a few weeks ago and everything is fine so far. I descided that i'd like to setup a tor (anonymous) server. I have 2 spare ip adress'.


I need to make sure that my regular/work ip is protected from my tor ip, so i need to somehow setup ubuntu to recognise i have multiple ip address', and then asign ONE to apache and another to tor. Right now the server only seems to respond to one of my ip's.


i really have no idea where to start with this, so any help would be appreciated.

---

### Post by HermanAB on 2007-09-01
Dunno about Tor, but the APache IP address to glom onto, is set in the Apache configuration file in /etc/httpd/conf/httpd.conf or some such.  By default, Apache will glom onto all addresses, so you need to find that line and change it - not difficult.  After changing it, yoiu have to restart Apache.

Cheers,

Herman

---

### Post by kudeta on 2007-09-03
Thanks very much for the reply. But does ubuntu need to be setup as wel in some simmilar way, to know how many ip addresses it has, becasue, as i said, the other ip's do not work whatsoever at the moment.

---

