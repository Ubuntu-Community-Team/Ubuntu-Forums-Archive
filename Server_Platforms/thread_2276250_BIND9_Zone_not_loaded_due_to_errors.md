---
title: "BIND9 Zone not loaded due to errors"
date: 2015-05-01
forum: Server Platforms
---

### Post by jingo_man on 2015-05-01
Hi all

I noticed that my local network's DNS started screwing up / not working last night. I have tried to use webmin to configure most things on this server, so this may be responsible. Anyway...


from the dans server itself, "nslookup server" results in:

> 
Server:		127.0.0.1
Address:	127.0.0.1#53


** server can't find jingoserver.jingo.local: SERVFAIL


So i looked in the /var/log/syslog (actually initially, i don't think any logging was working, but changed some logging settings for bind9 via webmin and now it is reporting stuff):

> 
May  1 09:25:34 jingoserver named[2873]: zone 0.in-addr.arpa/IN: loaded serial 1
May  1 09:25:34 jingoserver named[2873]: zone 127.in-addr.arpa/IN: loaded serial 1
May  1 09:25:34 jingoserver named[2873]: zone jingo.local/IN: journal rollforward failed: journal out of sync with zone
May  1 09:25:34 jingoserver named[2873]: zone jingo.local/IN: not loaded due to errors.
May  1 09:25:34 jingoserver named[2873]: zone localhost/IN: loaded serial 2
May  1 09:25:34 jingoserver named[2873]: zone 255.in-addr.arpa/IN: loaded serial 1
May  1 09:25:34 jingoserver named[2873]: zone 0.168.192.in-addr.arpa/IN: journal rollforward failed: journal out of sync with zone
May  1 09:25:34 jingoserver named[2873]: zone 0.168.192.in-addr.arpa/IN: not loaded due to errors.
May  1 09:25:34 jingoserver named[2873]: all zones loaded
May  1 09:25:34 jingoserver named[2873]: running


this is the contents of the /var/lib/bind/jingo.local.hosts file for this zone:

```

$ORIGIN .
$TTL 38400	; 10 hours 40 minutes
jingo.local	IN	SOA	jingoserver.jingo.local. dan.redswitch.co.uk. (
			1429522845
			10800
			3600
			604800
			38400 )
			NS	jingoserver.jingo.local.
$ORIGIN jingo.local.
$TTL 300	; 5 minutes
Dans-iPhone		A	192.168.0.53
			TXT	"3193a04367ecb26728379add688af113d0"
JINGOiPhone5S		A	192.168.0.52
			TXT	"316c723d6a6c67e1013faed123ca02370e"
$TTL 38400	; 10 hours 40 minutes
jingoserver		A	192.168.0.5
$TTL 300	; 5 minutes
OpenELEC		A	192.168.0.58
			TXT	"3192dae949679b9cc0950b49165d79df80"
jingoimac2.jingo.local.	IN	A	192.168.0.50

```

can anyone help figure out what part is causing the error(s) please?

thanks

jingo_man

---

