---
title: "Help with a centralized log server requested"
date: 2009-12-04
forum: Server Platforms
---

### Post by xkaliburx on 2009-12-04
In the past syslog on some old fedora machines worked fine, actually pretty simple addition to the syslog.conf server.

Those box's have been retired, the 8 new webservers are all running userver 8.10, syslog-ng comes out of the box.

I have found no real 'how-to' or example, but basically each webserver is a clone image and when debugging, it was nice to have one server to goto, and tail the real time logs.

So basically the question is, will syslog-ng alone allow me to have 8 servers write to a 9th (logging) type server, and if so, is anyone doing this, have some example config file for both syslog and the Apache vhost?

Thanks for the time.

---

