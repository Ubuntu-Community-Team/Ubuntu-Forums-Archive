---
title: "how to configure squid proxy under ubuntu 9.04 server"
date: 2009-11-06
forum: Server Platforms
---

### Post by mady03sam on 2009-11-06
hi buddies,
            im new to dis ubuntu so i need u ppl suggestions so tell me how to configure ma server with proxy server fcrse i recently installed squid init so how to configure ma server as a transparent proxy server

---

### Post by dvlchd3 on 2009-11-06
[http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

Hope this helps!

---

### Post by mady03sam on 2009-11-06
ur awesome man thanx for ur help buddy..................n ur helpin me a lot buddy

---

### Post by pandeylavakesh on 2009-11-17
Actually I am new to this Linux and so Ubuntu....what I did is that I installed Squid using Packet manager and left it as it was  I mean i didn't change anything.Everything was set by default.Once I deactivated it by Clicking DEACTIVATE radio button n it got deactivated..but when I am clicking on ACTIVATE button its not getting activated....So tell me where the hell is the problem????
What should I do now??
I can't restart my laptop because I am downloading Movies using Transmission Bit Torrent Client...
when I restart my system it doesn't resume but it starts from begining...is there any method to get it resumed after each startup...or something like that ...
thanks in advance.....[:P]

---

### Post by bertmanphx on 2009-11-17
Hello,
Try this:
Open a terminal screen, then type:

sudo /etc/init.d/squid restart

or

sudo /etc/init.d/squid stop
sudo /etc/init.d/squid start

See here
[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)

---

