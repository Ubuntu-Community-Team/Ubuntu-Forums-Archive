---
title: "Apache2 running but inaccessible locally or remotely (was working b4 today)"
date: 2006-04-24
forum: Server Platforms
---

### Post by bloodniece on 2006-04-24
I'm not sure what happened (hacker, me, other) 
I cannot reach any of the web sites hosted on my ubuntu server.
Neither localhost or mydomain.com works. The only thing that does work is Webmin running on port 10000. My NAT is setup to forward 80, 443, and 10000 to the Ubuntu box.
Stats:
Apache2
php5
mysql5
rails 1.12
static ip
5 virtual hosts running but inaccessible locally or remotely.
I have not changed permissions recently.

any help is appreciated.

---

### Post by Ensnared on 2006-04-24
As far as I know, webmin runs it's own webserver so even if that works it doesn't mean your main apache-server is actually running.

Just to make sure, did you try to restart it?```
sudo /etc/init.d/apache2 restart
```

Also, what is the error you get? Connection refused? Timed out? Not found?

---

### Post by bloodniece on 2006-04-24
thats the first thing I did.

no go

Forbidden

You don't have permission to access / on this server.

---

### Post by gymsmoke on 2006-04-24
run this at the commandline...

sudo apache2ctl configtest (paste the output)

if you get no errors (warnings are ok at this point)
sudo apache2ctl restart


then 
sudo tail /var/log/apache2/error.log
sudo tail /var/log/apache2/access.log

paste output along with your sites-available files...

---

### Post by bloodniece on 2006-04-28
In frustration, i backed up all sites and configs.
removed and reinstalled:
 bind9
apache2

and everything is fine.
 Maybe my bind was setup incorrectly. everything is running fine now.

:)

---

