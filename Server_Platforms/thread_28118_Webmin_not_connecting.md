---
title: "Webmin not connecting"
date: 2005-04-18
forum: Server Platforms
---

### Post by joebrandt on 2005-04-18
I have been running linux for a while now on my desktop.  I also have a server that I play with.  It had been running Mandrake 9.2 but I could not get e-mail working so I formatted it and loaded Ubuntu Warty.  As per the ubuntu-guide page I added the other repositories (all Hoary) and upgraded and updated untill nothing else was changed.  I apt-get(ted) webmin but access was denied.  I manually edited my hosts and hosts.allow files to include all nodes on my home network ... still denied.
I searchd the posts and removed webmin downloades the source and reinstalled from that (version 1.20) and access is still denied.  I have gotten to the certificate I checked accept permanently.  I did enable root password on server.  

Please help as I would like to get my website back online ASAP.
and add e-mail server...
and add nfs exports...
and share printer   (you get the idea)

Thanks in advance
Joe Brandt

---

### Post by blueplazma on 2005-04-18
Could you check in your logs?  I think it'll be /var/log/syslog.  See what the error is.

---

### Post by joebrandt on 2005-04-18
No mention in the log
several  "--MARK--" entries and cron jobs

I tried to login to webmin "lynx https://localhost:10000" and access was denied there also

---

### Post by blueplazma on 2005-04-19
[QUOTE=joebrandt]No mention in the log
several  "--MARK--" entries and cron jobs

I tried to login to webmin "lynx https://localhost:10000" and access was denied there also[/QUOTE]

A couple things could be your issue.  

First, it is possible that lynx doesn't support SSL.  I'm not sure.
Second, make sure that /etc/webmin/miniserv.users has a valid password root.  
Third, make sure that /etc/webmind/miniserv.conf has 127.0.0.1 or localhost listed as an approved client.

---

