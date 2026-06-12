---
title: "Start squid automatically with -D argument"
date: 2011-01-10
forum: Server Platforms
---

### Post by donelikedinner on 2011-01-10
Hello,

I am on Ubuntu 10.04, running Squid 2.7.STABLE7

Squid refuses to start on my machine unless I give it the -D argument (disable initial DNS tests). I think this is because my machine is offline while I'm testing it, so no DNS server.

Does anyone know how to set Upstart to start Squid with the -D argument?

Thanks!

---

### Post by iiz on 2011-01-10
I believe you can edit the init script in /etc/init.d/ add the switch to the start command. Though I am not sure if that's where the OS looks to for start up programs, it's worth a try :).


EDIT: just added this to my bind9 init script and rebooted, success it created ha.txt in / so the above should work.
```
echo starting bind>/ha.txt
```

---

### Post by liverpoolatnight on 2011-01-10
Try adding the DNS server to the squid.conf you can find this at /etc/squid/squid.conf

dns_nameserver 8.8.8.8 8.8.4.4 208.67.222.222 208.67.220.220

This will give you Google DNS & openDNS DNS services.
[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)
[www.opendns.com](www.opendns.com)

Dont forget to hit save, and restart squid ;) 

Hope this helps :)

---

