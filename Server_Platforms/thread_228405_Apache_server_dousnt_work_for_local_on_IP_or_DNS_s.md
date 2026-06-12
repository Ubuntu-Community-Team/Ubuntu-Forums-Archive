---
title: "Apache server dousnt work for local on IP or DNS serv."
date: 2006-08-03
forum: Server Platforms
---

### Post by FeestBijtje on 2006-08-03
Hello my DNS server is [http://feestbijtje.homedns.org/](http://feestbijtje.homedns.org/)
And every one claims they can connect to it but from my local machine it time's out... (not beeing able to connect)
And on my last install it worked all automaticly and worked all fine but now since a new install it dousnt work. Ive installed every thing like i am used to do it (as befor) and now i cannot access my server from [http://feestbijtje.homedns.org/](http://feestbijtje.homedns.org/) is there any solution for this problem?

---

### Post by Glut on 2006-08-03
*Edit* I can't connect to the address supplied, it times out too. The problem then most likely is your apache setup. Post /var/log/apache/error.log

---

### Post by FeestBijtje on 2006-08-04
Its not online 24/7 mabe you should try when i am online
Note: the log is empty

---

### Post by Sam on 2006-08-05
You can't access to your maching within your local network without adding it's name in /etc/hosts !

See [this thread](http://ubuntuforums.org/showthread.php?t=227892) for the answer.

---

### Post by FeestBijtje on 2006-08-07
Fixed thanx for the help... :)
Greetz...

---

