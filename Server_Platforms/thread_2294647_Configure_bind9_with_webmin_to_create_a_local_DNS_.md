---
title: "Configure bind9 with webmin to create a local DNS server with added particular zones"
date: 2015-09-12
forum: Server Platforms
---

### Post by dam034 on 2015-09-12
Good morning,

I have a VPS in my LAN with Ubuntu Server 14.04 and webmin.

I installed bind9 to have my DNS server, this server should redirect all requests to the root-servers DNS, except some I have to obscure them and a TLD of my LAN (eg. ".here").

Let me give an example:
```
server.here. A 192.168.1.11
printer.here. A 192.168.1.45
mtasa.here. CNAME server.here.
router.here. A 192.168.1.1
modem.here. CNAME router.here.
[FONT=Tahoma][COLOR=#333333]*--------------------------------------------*[/COLOR][/FONT]
www.obscured-site.com. CNAME server.here.
sub-domain.obscured-site.com. CNAME server.here.
```
I just installed bind9, and through webmin, I created a DNS zone like this:
```
here. NS 192.168.1.21
server.here. A 192.168.1.11
printer.here. A 192.168.1.45
mtasa.here. CNAME server.here.
```
For the record, 192.168.1.21 is the IP address of the VPS where bind9 it's installed.

I also set (only for the client from where I work), 192.168.1.21 as the DNS server for queries, but when I try to be here "server.here" he says nonexistent host.


Can I know what I did wrong in the current configuration and how to run correctly the sample configuration?

I think I mistaked in NS record.


Thanks,
dam034

---

### Post by darkod on 2015-09-12
Try to use ssh connection and the command line for controlling bind. I'm not sure if webmin is fully compatible. Many people try to use bind for its GUI but remember that it IS NOT an official and recommended tool, so full compatibility of the config files created by webmin is not guaranteed.

As for the few records you say you have created, the domain is specified by the zone file. After that when doing the A records you don't put the domain in them. Only the host name, the first part. So your A records should look something like:
```
server. A 192.168.1.11
```

The same goes for CNAME records. Again, since you are using webmin there might be some small differences, like with the trailing dots. I'm not sure you need them.

---

### Post by dam034 on 2015-09-13
I tried from command line to edit the files, I did so **named.conf.local**:
```
//// Do any local configuration here
//


// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";


zone "qui" {
    type master;
    file "/var/lib/bind/qui.hosts";
    };



```
And this is the file **/var/lib/bind/qui.hosts**:
```
$ttl 900@        IN    SOA    srvesp.qui. io.qui. (
            1441878291
            3600
            900
            604800
            900 )
@        IN    NS    172.31.6.123
server    IN    A    172.31.6.101
router    IN    A    172.31.6.1
wifi        IN    A    172.31.6.2
srvesp    IN    A    172.31.6.123
sut        IN    CNAME    server.qui.

```

When I start a simple Windows XP client and I set the DNS server of the LAN connection on the server where bind9 is installed, I try to open the windows command line and execute "ping ubuntuforums.org", and it works, but when I try to execute "ping server.qui", he says "nonexistant host".

Did I mistake anything?


Thanks,
dam034

---

### Post by darkod on 2015-09-13
First, you selected your zone to be only 'qui'. I'm no sure you can use dns like that, I have never actually tried setting it up unless it has at least domain name and tld like for example 'domain.tld'. In your case, and for a local private zone, can you maybe try with 'qui.local'?

Also in your qui.hosts you have error in the IN SOA definition. You put srvesp.qui. but it should be the domain with a trailing dot, without any machine name in front. So in your case 'qui.' or 'qui.local.'. That error will be messing up the zone definitions.

Also I suggest to name the zone file for example db.qui.local (db.domain.tld) instead of qui.hosts. Those are not only hosts in there and it is good practice to name it db because it's the database of the zone. You might as well create it in /etc/bind which is also good practice, instead of /var/lib. Something like /etc/bind/db.qui.local.

So, you will have:
named.conf.local
```
zone "qui.local" {
   type master;
   file "/etc/bind/db.qui.local";
};
```

/etc/bind/db.qui.local
```
$ttl 900
@   IN   SOA   qui.local. io.qui.local.   (
                    ......
                    ......)

@   IN   NS   srvesp.qui.local.
srvesp   IN   A   172.31.6.123
server   IN   A   172.31.6.101
router   IN   A   172.31.6.1
wifi   IN   A   172.31.6.2
sut   IN   CNAME   server
```

Try with something like that. Note that for IN NS you need FQDN hostname, not an IP. And that CNAME points to another existing A record without the domain suffix.

---

### Post by Doug S on 2015-09-13
I would recommend the [Ubuntu serverguide]("https://help.ubuntu.com/lts/serverguide/dns-troubleshooting.html") as a reference.
Also, there is no need to use CNAME at all, just allocate another A record for the same IP address. It will look up faster.

I used named checkzone on both files, the OP and darko's:```
doug@doug-64:~/config/bind/tempo$ named-checkzone qui qui.dam
qui.dam:8: NS record '172.31.6.123' appears to be an address
zone qui/IN: NS '172.31.6.123.qui' has no address records (A or AAAA)
zone qui/IN: not loaded due to errors.

doug@doug-64:~/config/bind/tempo$ named-checkzone qui qui.darko
zone qui/IN: loaded serial 1441878291
OK
```

---

### Post by dam034 on 2015-09-14
Considering that I am stubborn, and I wanted to force to the area of the first level (TLD) instead of a second, I was inspired by the answers of you darkod and Doug S, I did something like this:

[COLOR=#000000]**named.conf.local**
[/COLOR]```
zone "qui" {
type master;
file "/etc/bind/db.qui";
};

```
[COLOR=#000000]
[/COLOR][COLOR=#000000]**/etc/bind/db.qui**
[/COLOR]```
$ttl 900
@       IN      SOA     qui. io.qui. (
                        1441878291
                        3600
                        900
                        604800
                        900 )
@               IN      NS      srvesp.qui.
server          IN      A       172.31.6.101
router          IN      A       172.31.6.1
wifi            IN      A       172.31.6.2
srvesp          IN      A       172.31.6.123
s-rocco         IN      CNAME   server

```[COLOR=#000000]

[/COLOR]For this, thanks to you both, because without your answers, I wouldn't have solved the problem and I don't know what is the command "named-checkzone".


Thanks,
dam034


P.S.: just to know, "qui" (it) means "here" (en), and for this that I use it.

---

### Post by Doug S on 2015-09-14
> **dam034 said:**
>  and I don't know what is the command "named-checkzone".It is just a zone file validity checking tool. It is referred to in the link to the serverguide that I gave. By the way the "it" version of the the serverguide is virtually fully translated, something that is very rare for the severguide.

---

### Post by dam034 on 2015-09-14
Yes, in fact the serverguide has directly opened in italian.



Another question:
I want to create a zone where any subdomain will be traslated in an IP that I'll write.

Example of **/etc/bind/db.myzone.tld**:
```
$ttl 900
@               IN      SOA     myzone.tld. io.qui. (
                                1441878291
                                3600
                                900
                                604800
                                900 )
@           IN      NS      srvesp.qui.
@           IN      A       192.168.1.50
subdomain1  IN      A       192.168.1.50
subdomain2  IN      A       192.168.1.50
subdomain3  IN      A       192.168.1.50
...
any subdomain  IN      A       192.168.1.50

```
How can I do the resolution of *.myzone.tld in a single DNS record?



Thanks,
dam034

---

