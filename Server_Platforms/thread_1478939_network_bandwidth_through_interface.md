---
title: "network bandwidth through interface"
date: 2010-05-10
forum: Server Platforms
---

### Post by cong06 on 2010-05-10
I have a small network (~10 computers).
The router is an ubuntu computer which is also acting as a transparent proxy: Running apt-cacher and squid.

The two interfaces on the Ubuntu server are ppp0 and eth0. 

I would like to know the end total network bandwidth on ppp0, except:
1) Downloads with apt-cacher, ie: software updates
2) Any http requests initiated on the server computer (and other computers?), ie: web browsing on the server.

The reason is this:
The server is a internet cafe server, but also a server for computer installs. In order to more properly manage budgeting, I would like to keep track of how much bandwidth is going to what purpose.

One way of doing this might be to install a plugin into Firefox that keeps track of the bandwidth on that computer.
However, since the squid server is saving some because of caching, it'd be nice to count this in also.

Can iptables manage this?

---

### Post by TheFuturian on 2010-05-10
[ntop]("http://www.ntop.org/overview.html") should illustrate the information, however I'm not completely sure if it will handle your exceptions..

---

### Post by terazen on 2010-05-11
Try bandwidthd.  We use in on our pfsense boxes.  I'm not sure if it satisfies everything you are wanting, but it might suffice.

---

### Post by cong06 on 2010-05-21
I can't get bandwidthd to work.
I installed it, ran "/etc/init.d/bandwidthd start", let it run for a while but still:
file:///var/lib/bandwidthd/htdocs/index.html
isn't updated.

It suggested a "README" but I can't find it.

---

