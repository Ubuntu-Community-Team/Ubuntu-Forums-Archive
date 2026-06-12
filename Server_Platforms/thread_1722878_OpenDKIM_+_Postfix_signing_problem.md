---
title: "OpenDKIM + Postfix signing problem"
date: 2011-04-06
forum: Server Platforms
---

### Post by patrickstolc on 2011-04-06
Hi everyone,

I'm having problems signing my outgoing emails. I'm using Postfix + OpenDKIM, and experience problems when trying to use anything other than localhost as a host.

Ex.

telnet localhost 25 - works
telnet domain.com 25 - dosn't work
telnet ip-adress 25 - dosn't work

It is sending the email in all cases, but only signing it when connecting through localhost.

Hope someone can help. Thanks :)

---

### Post by pindari on 2012-06-08
Make sure your InternalHosts file is correctly configured.

within **/etc/opendkim.conf** you should have something like

*InternalHosts /var/db/dkim/internal_hosts*

and then the file referenced should look like

# cat /var/db/dkim/internal_hosts
[I]127.0.0.1
x.x.x.x/xx[/I]

where x.x.x.x/xx is your range of IP numbers.

more info at [http://family.pindari.com/index.php/OpenDKIM](http://family.pindari.com/index.php/OpenDKIM)

---

