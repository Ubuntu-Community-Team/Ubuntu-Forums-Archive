---
title: "ddclient multiple servers"
date: 2008-02-02
forum: Server Platforms
---

### Post by mikesoft on 2008-02-02
Hello,

I use ddclient for my site, using dnspark.com as server, but now I also have another domain name (using dyndns) and I want it to point to the same IP address, I know how to configure /etc/ddclient.conf for one or for another, but how can I configure it so it can update dyndns and also dnspark at the same time?

this is how it looks right now:

daemon=300
syslog=yes
pid=/var/run/ddclient.pid
protocol=dnspark
use=web, web=ipdetect.dnspark.com, web-skip='Current Adress: '
server=www.dnspark.com
login=user
password='password'
domain.com

the above settings updates the IP for domain.com using dnspark, and I want to add a new domain name that uses dyndns, domain.servegame.org for example.

 I hope I made myself understandable.

Thanks.

---

### Post by Hypatia2 on 2008-03-26
I'm looking for a way to do the same thing.  Has anyone figured it out?

---

### Post by dmizer on 2008-03-26
here's my config (it's dyndns instead of dnspark, but the config is still the same):

```
pid=/var/run/ddclient.pid
protocol=dyndns2
use=web, if=checkip.dyndns.com/, web-skip='IP Address'
server=members.dyndns.org
login=user
password='pass'
domain1.net,domain2.com,domain3.org
```

oops, you mean you want to use both dyndns and dnspark.  try this config:
```
daemon=300
syslog=yes
pid=/var/run/ddclient.pid
use=web, web=ipdetect.dnspark.com, web-skip='Current Adress: '
protocol=dnspark
server=www.dnspark.com
login=dnspark-username
password='dnspark-pass'
domain1.com
protocol=dyndns2
server=members.dyndns.org
login=dyndns-username
password='dyndns-pass'
domain2.net
```

don't know for sure if that will work or not, but the configuration should be something similar to that.

---

### Post by shane2peru on 2008-05-13
> **dmizer said:**
> here's my config (it's dyndns instead of dnspark, but the config is still the same):

```
pid=/var/run/ddclient.pid
protocol=dyndns2
use=web, if=checkip.dyndns.com/, web-skip='IP Address'
server=members.dyndns.org
login=user
password='pass'
domain1.net,domain2.com,domain3.org
```

oops, you mean you want to use both dyndns and dnspark.  try this config:
```
daemon=300
syslog=yes
pid=/var/run/ddclient.pid
use=web, web=ipdetect.dnspark.com, web-skip='Current Adress: '
protocol=dnspark
server=www.dnspark.com
login=dnspark-username
password='dnspark-pass'
domain1.com
protocol=dyndns2
server=members.dyndns.org
login=dyndns-username
password='dyndns-pass'
domain2.net
```

don't know for sure if that will work or not, but the configuration should be something similar to that.

Ok, quick question I set this up this way, and it seems to be working with the file setup following the above example.  However I have a question.  with the daemon=600 line in there, does that automatically set it up to run as a daemon, therefore, every 10 minutes it would continue to check and make sure the ip address is correct?   Or do I need to set this up as a root cron job to run every 20min or so???  Thanks.

Shane

---

