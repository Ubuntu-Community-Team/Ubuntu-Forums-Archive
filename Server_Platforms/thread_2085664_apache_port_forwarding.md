---
title: "apache port forwarding"
date: 2012-11-18
forum: Server Platforms
---

### Post by spillage2 on 2012-11-18
Hi All,

Ok I have set up a couple of webservers 12.04 on virtualbox. These are just for testing and stuff so nothing to serious.

The first one was working fine but as it goes I started playing with webmin and things went a bit wrong..

So I set up the second server and set up port forwarding on my router...could not gain access from the outside world. After a while looking around I decided the remove the setting from my router for the first server and bingo it all works.

Question: I have a draytek router..is it possible to run two servers through one router or would I need to use port 8080?

cheers spill.

---

### Post by darkod on 2012-11-18
You can't forward the same port to two different private IPs.

Also, unless the people accessing from the outside know to use different port, you can't really set up two different webservers behind the same router (public IP). How will it know what traffic for port 80 to forward to which server?

Without using a different port from the outside, any browser will send the http traffic on port 80. They don't use 8080 or whatever, unless specifically told to.

---

### Post by spillage2 on 2012-11-18
ok thanks that kinda what I thought.

---

### Post by SeijiSensei on 2012-11-20
You can still create an unlimited number of virtual servers on a single IP using [name-based virtual hosting]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html").

---

### Post by spynappels on 2012-11-20
And don't forget that if you specifically need to use separate servers for different websites, you can forward port 80 to one, and use it as a reverse proxy to the other.

---

