---
title: "utility to monitor web server status"
date: 2008-11-05
forum: Server Platforms
---

### Post by pytheas22 on 2008-11-05
I'm looking for a program that can monitor a remote server and send me email if it thinks that the ssh, ftp or http services on the remove server are down.  Ideally, it would be able to send the mail using a remote mail server, like gmail (because I don't want to set up a mail server on the machine that's running the monitoring program).  I've heard of things to do this but can't seem to find any now.  Does anyone have suggestions?  Thanks in advance.

---

### Post by CrucifiedEgo on 2008-11-05
try mon.itor.us -- i've used that in the past.

There's also the option of writing your own script to do it as well, or using a premade one (google is your friend there -- there's hundreds out there)

---

### Post by baudday on 2008-11-05
[http://bash.cyberciti.biz/monitoring/monitor-unix-linux-network-services/](http://bash.cyberciti.biz/monitoring/monitor-unix-linux-network-services/)

That look good?

---

### Post by pytheas22 on 2008-11-07
Thanks for the answers.  moni.tor.us looks nice but is really more sophisticated than I need.  The bash script was also not bad, although I will need to modify it a bit if I want to use it to address oddities on our old Red Hat server, plus I would really like to be able to monitor http and ssh on our web server from a remote machine...so that if the whole server goes down for some reason, I'd still know about it.

---

