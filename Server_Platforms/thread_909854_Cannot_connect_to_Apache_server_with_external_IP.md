---
title: "Cannot connect to Apache server with external IP"
date: 2008-09-03
forum: Server Platforms
---

### Post by frmdstryr on 2008-09-03
Hi, I recently set up an apache2 webserver.  At first it was viewable over the internet but I must have messed something up because now it is only viewable locally and by my lan (i tried reinstalling apache, no luck).  For some reason my main directory is protected, but my other directories within that can be seen.  My router is set to forward port 80 to the server.  It cannot be accessed via domain or ip. Canyouseeme.org reports "Error: I could not see yours service, Reason: Connection timed out"

Any help is appreciated, thanks.

---

### Post by windependence on 2008-09-04
Please post your apache2.conf file for us. Doesn't seem like the server is listening on 80.

Just a note: I don't know why everyone has to "reinstall" everything. That is sooo Windoze. If you have a problem, post it here and we will fix it instead of just blowing everything away. Sometimes, you can actually cause more problems by doing this on a Linux box. ;)

-Tim

---

### Post by frmdstryr on 2008-09-04
Okay here it is...

---

### Post by JKHinton CPBD on 2008-09-04
Hello frmdstryr & windependence,

I am a new user was reading your post, I also just installed Ubuntu LAMP server,  I then installed Kubuntu. When you said Apache was viewable on the web are you using Webmin to view Apache2.conf? I've installed Webmin and thought it was supposed to let you configure Apache config file but its not finding the file. I then went to adept the repository manager and installed everything that it would let me that said Apache Documents.
I know this sounds like a crazy question but I found in Services Window(under system, Administration) that Apache2 is running on my system.  I did a search on Dolphin file manager file://with a check mark to search all subdirectories trying to find Apache2.conf I also tried file://user/local/apache with no luck.  Can ya'll tell me where to find the apache2.conf file?

Thank you

---

### Post by mbeach on 2008-09-04
under normal circumstances it is found at:
/etc/apache2/apache2.conf

---

### Post by lmno149 on 2008-09-04
[eve online isk](http://games.groups.yahoo.com/group/eve_online_isk/)[eq2 plat](http://games.groups.yahoo.com/group/eq2_plat/)[final fantasy xi gil](http://games.groups.yahoo.com/group/final_fantasy_xi_gil/)[guild wars gold](http://games.groups.yahoo.com/group/guild_wars_gold/)[l2 adena](http://games.groups.yahoo.com/group/l2_adena/)

---

### Post by frmdstryr on 2008-09-04
I found out what it was, my ISP was blocking port 80, and when I changed my ports.conf I was forgetting to change my port forwarding as well.  Thanks!

---

### Post by cariboo on 2008-09-05
JKHinton CPBD

Almost all configuration files are in /etc. the easiest way to find is is to open a terminal (not sure how to do it in Kubuntu) and type:

```
cd /etc/apache2
```

then to show a listing of the files in that directory in the same terminal:

```
ls -l
```

To edit apache2.conf, in a terminal:

```
sudo nano /etc/apache2/apache2.conf
```

Jim

---

