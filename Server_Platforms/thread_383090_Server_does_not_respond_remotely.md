---
title: "Server does not respond remotely"
date: 2007-03-12
forum: Server Platforms
---

### Post by nuzzlenut on 2007-03-12
Hello everyone. My first post. I have a 6.06 server. Running Apache, FTP, and simple file/print services at home. I have always been able to Putty into it from my internal network computers. I recently set myself up with a No-ip.com site and have been playing with it remotely. The odd thing is that after a few days of the server being up it does not respond to the site anymore and I can no longer Putty into it. It ran for months without issue and now I can restart it and a few days later my connections will start to timeout and I have to restart again. I am not sure where to even start to diagnose this issue and would appreciate some help.

Thanks,
Josh

---

### Post by Mr. C. on 2007-03-12
This is curious.  Here are some things I would do:

1) examine your logs for any obvious problems
2) determine if there is an correlation to IP address changes
3) check netstat -an, and look at the ssh connections.  Are there many ssh clients in timeout?  Could be denial of service attacks.
4) check ps to see how many ssh processes are running

This should be a good start.
MrC

---

### Post by nuzzlenut on 2007-03-15
Thanks Mr. C. I started to dig into and just started over with a fresh install. I realized it was not set up the way I wanted it anyway.

---

