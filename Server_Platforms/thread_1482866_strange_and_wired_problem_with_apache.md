---
title: "strange and wired problem with apache"
date: 2010-05-14
forum: Server Platforms
---

### Post by trylik on 2010-05-14
hi

i have ubuntu server 10.04 on my dedicated server in ovh

i have bind on it

i installed a domain for server IP and everything looks OK, but not on firefox (only firefox, not opera or even lynx)

when i type "example.com" in firefox i can see local (on my client not on dedicated server) /var/www content (i also have locally installed lamp)

but when i type "www.example.com" everything is OK
this is so weird, have you seen something like that before?



my conf:

BIND9
named.conf.default-zones

[...]

zone "domena.pl" {
       type master;
       file "/etc/bind/db.domena.pl";
       allow-transfer { 213.186.33.199; };
       notify yes;
};

zone "localhost" {
       type master;
       file "/etc/bind/db.local";
};

[...]

db.domena.pl
;
; BIND data file for domena.pl
;
$TTL    604800
@       IN      SOA     ns.domena.pl. root.domena.pl. (
                       2010051305      ; Serial
                        604800         ; Refresh
                         86400         ; Retry
                       2419200         ; Expire
                        604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.domena.pl.
@       IN      A       188.165.xx.xx
www     IN      A       188.165.xx.xx
beta    IN      A       188.165.xx.xx
ns      IN      A       188.165.xx.xx
@       IN      AAAA    ::1
;

vhosts on apache

httpd.conf:
NameVirtualHost 188.165.xx.xx:80

<VirtualHost 188.165.xx.xx:80>
 ServerName domena.pl
 ServerAlias [www.domena.pl](www.domena.pl)
 DocumentRoot /var/www
 # log
 ErrorLog  /var/log/apache2/domena.pl-error.log
 CustomLog /var/log/apache2/domena.pl-access.log combined

</VirtualHost>

######
/etc/hosts
# Do not remove the following line, or various programs
# that require network functionality will fail.
127.0.0.1       localhost.localdomain localhost
188.165.xx.xx   ks310891.kimsufi.com
188.165.xx.xx  domena.pl
# The following lines are desirable for IPv6 capable hosts
#(added automatically by netbase upgrade)
::1     ip6-localhost ip6-loopback
feo0::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
########
/etc/resolv.conf
domain domena.pl
nameserver 188.165.xx.xx
nameserver 213.186.33.99
search ovh.net

---

### Post by cdenley on 2010-05-14
> **trylik said:**
> 
when i type "example.com" in firefox **i can see local (on my client not on dedicated server) /var/www content** (i also have locally installed lamp)

What does that mean?

If firefox appears to show different content than your other browsers, then it is probably displaying cached content.

---

