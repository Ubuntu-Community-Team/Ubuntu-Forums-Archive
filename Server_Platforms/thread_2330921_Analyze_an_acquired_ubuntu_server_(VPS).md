---
title: "Analyze an acquired ubuntu server (VPS)"
date: 2016-07-16
forum: Server Platforms
---

### Post by lefataliste on 2016-07-16
Hi,
i'm not sure how to look for this topic, so I hope i'm not repeating and old topic.

I recently acquired from a client of mine a VPS (mainly as websites hosting). The old sys manager disappeared so I have no idea what has happened on the VPS in the last years.
I'd like to have a clear picture of the situation (software installed, users, groups and other stuff that could be usefull to avoid surprises in the future).

At the moment I've checked /etc/groups, users and shadows and /etc again for installed software.
I alse checked cron to see what's going, /var/www for website installed. 

Any other suggestion? Am i missing something?

Thanks

---

### Post by frostschutz on 2016-07-17
Is this about not knowing what the machine is supposed to be doing (which services are running, how things work)?

Or worry whether or not the machine might have been compromised or giving access to people who no longer work for the company?

In the latter case the only option is to reinstall from scratch. There is so many ways to hide malware/backdoors in a system, once compromised you can't trust it anymore, reinstall is the only option.

---

### Post by lefataliste on 2016-07-17
Hi! Thanks for the reply.
I'm evaluating both issues, both security-side and software/services-side.

---

### Post by SeijiSensei on 2016-07-19
To see what services are exposed, I suggest installing **nmap** on another computer and using it to scan the server for open ports.  You should see what it is supposed to be providing. For instance,
```

$ sudo nmap -sT www.ubuntuforums.org
Nmap scan report for www.ubuntuforums.org (91.189.94.12)
Host is up (0.063s latency).
Other addresses for www.ubuntuforums.org (not scanned): 91.189.94.16
rDNS record for 91.189.94.12: feijoa.canonical.com
Scanned at 2016-07-19 13:42:33 EDT for 14s
Not shown: 996 filtered ports
PORT     STATE SERVICE
80/tcp   open  http
443/tcp  open  https
554/tcp  open  rtsp

```

---

### Post by Habitual on 2016-07-20
> **lefataliste said:**
> Am i missing something?
Yes, A sysadmin. :)

What a "guy", gave you a webhost full of unknowns.
It's is still hosting these "sites"?

```
sudo du -sh /var/lib/mysql/
``` will show you general database disk usage.
```
mysql -uroot -p -e "show databases;"
``` will show you the dbs.

To "see" what's Listening" on the host, run 
```
sudo netstat -ta | grep LISTEN
```

Let us know.

---

