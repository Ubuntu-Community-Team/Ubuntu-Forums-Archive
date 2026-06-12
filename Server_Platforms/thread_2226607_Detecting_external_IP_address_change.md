---
title: "Detecting external IP address change"
date: 2014-05-28
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2014-05-28
Hi all

Have a client with a dynamic IP address.

Every 5 minutes a script is executed that checks for a change in the external IP address through a CRON job
```
*/5 * * * * /var/data/bin/zoneedit.sh
```

If the address has changed, then [www.zoneedit.com](www.zoneedit.com) is updated with the new IP address.

```
#!/bin/bash

ipfile='/var/data/bin/ipaddress'

[[ -f "$ipfile" ]] && ipold="$(< "$ipfile" )"
ipnew="$( wget -q -O - checkip.dyndns.org | sed -e 's/.*Current IP Address: //;s/<.*$//' )"

if [[ "$ipold" != "$ipnew" ]]; then......

fi
```

This works but there maybe a 5 minute delay, at maximum, before the update takes place.

Are there any alternative ways to detect an external IP address change and thus cause the second part of the script to run?

TIA

---

### Post by matt_symes on 2014-05-28
Hi

Is the box directly connected to the internet or behind a router with port forwarding ?

You're running ubuntu and dhclient ?

Kind regards

---

### Post by ChrisRChamberlain on 2014-05-28
matt_symes

Thanks for your reply.

Behind a router with port forwarding

Ubuntu yes, 
dhclient no.

---

### Post by pqwoerituytrueiwoq on 2014-05-28
you can mod the script i made:
[http://pastebin.com/16jKus3r](http://pastebin.com/16jKus3r)
here is a script a person made that uses multiple ip checkers 
[https://github.com/tknorris/duckdns/blob/master/duckdns_upd_ip.sh](https://github.com/tknorris/duckdns/blob/master/duckdns_upd_ip.sh)

---

### Post by sandyd on 2014-05-28
What model of router do you have?

ddclient can access the status page of *some* routers and get the ip from there.

---

### Post by ChrisRChamberlain on 2014-05-28
pqwoerituytrueiwoq 

Thanks for your reply - will take a look

sandyd

Thanks for your reply - Netgear DG834G

---

### Post by sandyd on 2014-05-28
> **ChrisRChamberlain said:**
> pqwoerituytrueiwoq 

Thanks for your reply - will take a look

sandyd

Thanks for your reply - Netgear DG834G

Yes, that router should work fine.

You will have to configure ddclient to read the ip from the router status page - [here is a page]("https://github.com/wimpunk/ddclient") on how to do it (will need to scroll down a bit)

---

### Post by ChrisRChamberlain on 2014-05-29
sandyd

Many thanks - will go figure it out

---

### Post by ChrisRChamberlain on 2014-06-02
sandyd

Thanks for resolving the question> Are there any alternative ways to detect an external IP address change...

In this instance and with this router, it provides a solution.

However in the long term it may not as the router may change and not be supported.

Am going to rewrite the first part of the script and error trap variables with a length of 0, etc, which will prevent the second half being executed.

Also going to add an alternative to ```
ipnew="$( wget -q -O - checkip.dyndns.org | sed -e 's/.*Current IP Address: //;s/<.*$//' )"
``` using ```
ipnew="$( curl ident.me )"
```which should also prevent the second half being executed if no IP address is returned.

This also means the time interval can be reduced to three minutes so either external resource is 'polled' only every six minutes.

---

