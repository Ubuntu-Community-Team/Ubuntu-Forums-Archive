---
title: "Bind9 error with &quot;root domains&quot;"
date: 2006-08-20
forum: Server Platforms
---

### Post by insulae on 2006-08-20
(first sorry for my english, my primary language is spanish)

i have a ubuntu dapper server **for a intranet only**.
i need to create a "root domain(?)" only like: [http://virtual](http://virtual) , i dont want [http://virtual.com](http://virtual.com) or [http://virtual.localdomain](http://virtual.localdomain) , i need only [http://virtual](http://virtual) 

so i create the next configuration:

in file /etc/bind/named.conf 

```
zone "virtual" {
        type master;
        file "/etc/bind/db.virtual";
};

```

in file /etc/bind/db.virtual

```
$TTL    604800
@       IN      SOA     virtual. virtual. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@               IN      NS      localhost.

virtual.        IN      A       1.1.1.253
www             IN      A       1.1.1.253

```

or 

```
$TTL    604800
@       IN      SOA     ns.localhost. root.localhost. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@               IN      NS      ns
virtual.        IN      A       1.1.1.253
```


when i run from linux client:

nslookup virtual

```

Server: 1.1.1.253
Address:  1.1.1.253#53

Name:  virtual
Address:  1.1.1.253[/B]

```

when i run from linux client:

ping virtual

```

PING virtual (1.1.1.253) 56(84) bytes of data.
64 bytes from 1.1.1.253: icmp_seq=1 ttl=64 time=0.213 ms
64 bytes from 1.1.1.253: icmp_seq=2 ttl=64 time=0.315 ms

```

when i try to see the web page in firefox or konqueror with [http://virtual](http://virtual) is everything ok!! i see the web perfectly

**so what is my problem?**

when i try to see the web page from a windows client, with iexplorer or firefox i can't see anything.

if i run from windows client:

nslookup virtual 

```

Server: 1.1.1.253
Address:  1.1.1.253#53

Name:  virtual
Address:  1.1.1.253[/B]

```

the nslookup is ok, but if i try to do a ping to virtual i dont receive any response, but if a execute a ping to [www.virtual](www.virtual) or virtual. i have response!!, and now if i try to go via iexplorer to [http://virtual](http://virtual) i can see the page.

i don't know what to do, i read many pages in google but i dont have any response.

---

### Post by chrisfay on 2006-08-20
This may be way to obvious but did you set your nameservers in your windows cliet to the ip of your dns server?

---

### Post by insulae on 2006-08-20
> **chrisfay said:**
> This may be way to obvious but did you set your nameservers in your windows cliet to the ip of your dns server?

yes the windows client is set to my bind9 dns server, remember this:

from a windows client:
if i try to go in to [http://virtual](http://virtual) , i can't
then if i try to go in to [http://www.virtual](http://www.virtual) , i can
and then i try to go in to [http://virtual](http://virtual) and now i can!!! hehehe

the windows client configuration is:
```
ip  1.1.1.16
netmask 255.255.255.0
gateway 1.1.1.253
dns1 1.1.1.253
dns2 NO
```

---

### Post by sysops on 2006-08-22
hi insulae,

there are 2 potential 'errors' in your setup that might confuse DNS lookups and IP routing on your clients.

1. You seem to be using a public address range for your network i.e. 1.1.1.x, most network hosts will think this range exists somewhere on the internet and  forward all traffic destined to it through to your network's gateway/router. so even though you would expect your clients to assume the server at [http://virtual](http://virtual) is on the same segment, they are actually looking for this host outside your network.

Resolution: change your addressing to use a private address range i.e. 10.x.x.x OR 172.16-32.x.x OR 192.168.x.x, that way, your network gateway will recieve IP traffic for this range and forward it on to the right destination(s).

2. Using a Zone that has no TLD is not recommended as the setup to get it working right is complex and unecessary. It is not recommended for the very same reasons, having said that, there is nothing to stop you from using it if you really want to. But i would advise you to use a TLD such as ".local" lest you want to end up pulling your hair out each time you setup or do anything DNS related.

Resolution : use a TLD such as .LOCAL so that you end up with an effective domain name as VIRTUAL.LOCAL. I know you would like to be able to access hosts just by hostnames such as [http://virtual](http://virtual). So if you setup bind right and associate A records with the hostname virtual, you should be able to use the same URLs without any loss of functionality.

A good reason to use TLD/root zone is because clients base lookups based on the "Primary DNS suffix" assigned to them. For example, if you assign a primary DNS suffix of VIRTUAL.LOCAL to your clients and if you attempt to d o something like ping www or [http://www](http://www), the name resolver automatically appends VIRTUAL.LOCAL to that query to lookup [WWW.VIRTUAL.LOCAL](WWW.VIRTUAL.LOCAL) on the DNS server. In your current setup, you have no suffix (well, actually you do but it's . which conflicts with the public one of the same suffix which is more of a reason to switch to avoid ambiguity).

I don't mean to tell you what to do, i just think you will save yourself time and hassle if you setup the network addressing and naming correctly.

Cheers,

Sysops

---

