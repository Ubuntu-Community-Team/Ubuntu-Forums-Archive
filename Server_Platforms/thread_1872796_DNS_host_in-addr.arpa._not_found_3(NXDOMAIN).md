---
title: "DNS: host in-addr.arpa. not found: 3(NXDOMAIN)"
date: 2011-10-31
forum: Server Platforms
---

### Post by veggis on 2011-10-31
reverse dns not working

named-checkzone example.lan /etc/bind/zones/db.172
zone example.lan/IN loaded serial xxxxxxxx
OK

but
root@example: host 172.21.100.100
host 100.100.21.172.in-addr.arpa. not found: 3(NXDOMAIN)

my reverse dns file 

```
$TTL    604800
@       IN      SOA     example.lan. me.somewhere.somewhere. (
                        xxxxxxxx      ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      example.
21      IN      PTR     ns1.example.lan.

```someone got any ide?

---

### Post by SeijiSensei on 2011-10-31
We'd need to see what you have as the entry for the reverse domain in named.conf, but it should look like this:

```

zone "100.21.172.in-addr.arpa" {
     type master;
     file "/path/to/your/zonefile";
};

```

Then in the zone file you'd have an entry for the .100 host like this:

```
100     IN     PTR    somehost.example.lan.
```

The file you display above has only a host entry for the nameserver.  I can't tell which subnet it's supposed to be the zone file for, but I'm guessing you tried "21.172.in-addr.arpa" rather than "100.21.172.in-addr.arpa".

---

### Post by Rakeshvijayan on 2011-10-31
> **SeijiSensei said:**
> @       IN      NS      example. 21      IN      PTR     ns1.example.lan.


where is your server ip and what is your intention to do please mention it first

[https://help.ubuntu.com/11.10/serverguide/C/dns-configuration.html](https://help.ubuntu.com/11.10/serverguide/C/dns-configuration.html) use this link to configure dns ,only thing that you want to do is change domain name and give ip of corresponding client on reverse zone .dont panic we are here to help you

---

### Post by veggis on 2011-11-01
The fault was as [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") pointed:
[CODE10     IN      PTR     peter.elevnet.lan.
insteed of 100     IN      PTR     peter.elevnet.lan.][/CODE]

and in the named.conf.local

```
zone "21.100.172.in-addr.arpa"
{
        type master;
        notify no;
        file "/etc/bind/zones/db.172";
};
insteed of 
zone "100.21.172.in-addr.arpa"
{
        type master;
        notify no;
        file "/etc/bind/zones/db.172";
};



```

so thank for the help:o

---

