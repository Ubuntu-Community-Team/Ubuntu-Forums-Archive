---
title: "BIND9 not allowing forwarding requests for clients?"
date: 2009-03-26
forum: Server Platforms
---

### Post by digimars on 2009-03-26
OK, I've been trying my hardest to figure this out.

I have BIND9 installed and set up as a slave to one of our Domain Controllers (so we can at least still get DNS if it were to go down).  It works fine for transferring the zone file of our domain down, and from the server running BIND I can resolve hostnames of our local network machines along with outside names such as google.com (using nslookup, yeah I know it sucks).

However, when I set up one of my Windows XP clients to use the new server for DNS, it can resolve local machine names fine when I run nslookup against it, but it gives me "Query refused" when trying to resolve an outside DNS name.

I ran nslookup against the ISP's DNS IP's and can resolve the outside hostnames just fine, but for some reason I can't resolve them against the new DNS server.

I have not made any modifications to /etc/bind/named.conf.  Instead, I have put my configurations in /etc/bind/named.conf.local (since that is what the named.conf file says to do).

Here is my /etc/bind/named.conf.local file (protected of course):
```

zone "OURDOMAIN.COM" {
       type slave;
       masters {
                192.168.1.22;
                192.168.1.23;
       };
       file "OURDOMAIN.COM.db";
       allow-transfer {
                any;
       };
       allow-query {
                any;
       };
};

zone "192.168.in-addr.arpa" {
       type slave;
       masters {
                192.168.1.22;
                192.168.1.23;
       };
       file "192.168.in-addr.arpa.db";
       allow-transfer {
                any;
       };
       allow-query {
                any;
       };
};

```

And my /etc/bind/named.conf.options:

```

options {
        directory "/var/cache/bind";

        forwarders {
                   216.12.0.20;
                   216.12.48.23;
        };

        auth-nxdomain no;
        listen-on-v6 { any; };
};

```

Again, this only seems to affect outside clients, I can run queries on nslookup just fine on the DNS server itself.

Any help would be greatly appreciated.

---

### Post by netztier on 2009-03-26
> **digimars said:**
> but it gives me "Query refused" when trying to resolve an outside DNS name. 

Are the subnets where those XP clients live listed in the option **allow-recursion {...}** ? A common name resolver (aka "DNS client") will do what is called **recursive queries**: "Please dear DNS, tell me what is the IP address of www.ourdomain.com" and will let the DNS server do the job of finding the right DNS server to query.

So a DNS server querying another server will do an **iterative query**: "hey there main DNS server of .com, can you please let me know which is the server I should go and ask for information about ourdomain.com?"

Normally, you don't want your own DNS to accept recursive queries (which generate workload for your server) from just anyone. Hence there is the option **allow-recursion {}** so that you can limit the range of addresses that are allowed to query recursively.


**allow-recursion{}** should be in /etc/bind/named.conf.options

> 
Again, this only seems to affect outside clients, I can run queries on nslookup just fine on the DNS server itself.


Testing with nslookup from the shell (of the system that runs BIND) might not deliver expected results. If you use nslookup, it will refer to /etc/resolv.conf and ask the first DNS server listed in there. If that's not 127.0.0.1 or your server's own IP address, the query goes to somewhere else and gets whatever answer comes from there - which might be false.

Rather use **dig @<dnsserver> <name> <type>** to test DNS lookup, where:

[LIST]
[*]<**dnsserver**> is the IP address of the DNS server you want to query; in our case, this might be localhost, 127.0.0.1 or your server's own IP address
[*]<**name**> is the domain name you want to lookup, eg **ourdomain.com**
[*]<**type**> is the record type you want to query, such as **A**, **AAAA**, **MX**, **NS** or **SOA**
[/LIST]

---

### Post by netztier on 2009-03-26
> **digimars said:**
> 
```

zone "OURDOMAIN.COM" {
       type slave;
       masters {
                192.168.1.22;
                192.168.1.23;
       };
       [COLOR="Red"]file "OURDOMAIN.COM.db";[/COLOR]
       allow-transfer {
                any;
       };
       allow-query {
                any;
       };
};

zone "192.168.in-addr.arpa" {
       type slave;
       masters {
                192.168.1.22;
                192.168.1.23;
       };
       [COLOR="Red"]file "192.168.in-addr.arpa.db";[/COLOR]
       allow-transfer {
                any;
       };
       allow-query {
                any;
       };
};

```


Oh.. and while you're at it - check /var/log/syslog after restarting BIND to see if it isn't complaining about not finding it's .db files. It might be that they need to be specified with an absoulte path like

```
file "/etc/bind/zonefiles/OURDOMAIN.COM.db";
```

Adapt the path to reflect the file's actual location on your system - some admins prefer to have the database files somwhere like /var/bind/ or /var/named/ instead of /etc/bind/.

regards

Marc

---

### Post by digimars on 2009-03-26
Thanks!  Enabling recursion was what I needed!  Also, thanks for the tip on dig, after I thought about it more I realized that using nslookup on the server itself wasn't telling me anything useful for my exact problem.

---

### Post by digimars on 2009-03-26
> **netztier said:**
> Oh.. and while you're at it - check /var/log/syslog after restarting BIND to see if it isn't complaining about not finding it's .db files. It might be that they need to be specified with an absoulte path like

```
file "/etc/bind/zonefiles/OURDOMAIN.COM.db";
```

Adapt the path to reflect the file's actual location on your system - some admins prefer to have the database files somwhere like /var/bind/ or /var/named/ instead of /etc/bind/.

regards

Marc

Thanks, I actually have that set in my options file to go to /var/cache/bind.  I remember reading somewhere that storing these things in /etc/bind was a rather bad idea.

Again, I appreciate the help!!

---

