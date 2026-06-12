---
title: "Bind9"
date: 2008-01-14
forum: Server Platforms
---

### Post by tsikis on 2008-01-14
Hello there i tried to configure bind9 but i have the same problem all the time no matter what changes i make to the configuration files.
i  put in the named.conf.local the :
one "mydomain.com" {
        type master;
        file "/etc/bind/zones/mydomain.com.db";
        };
zone "0.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.0.168.192.in-addr.arpa";
};
because my router has address 192.168.0.1
afterwards i changed named.conf.options
and put:
forwarders {
     
      ip.of.my.ispdns;
};
then sudo mkdir /etc/bind/zones
edited the
/etc/bind/zones/mydomain.com.db

with :

// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
mydomain.com.      IN      SOA     ns1.mydomain.com. admin.mydomain.com. (
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
mydomain.      IN      NS              ns1.mydomain.com.
mydomain.      IN      MX     10       mta.mydomain.com.

// Replace the IP address with the right IP addresses.
www              IN      A       192.168.0.101
mta              IN      A       192.168.0.100
ns1              IN      A       192.168.0.3

192.168.0.100 and 101 dont exist i just dont have a mail server.
created end edited /etc/bind/zones/rev.0.168.192.in-addr.arpa
with:
//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
@ IN SOA ns1.mydomain.com. admin.mydomain.com. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     ns1.mydomain.com.
3                    IN    PTR    mydomain.com


edited the /etc/resolv.conf
with:
search mydomain.com
nameserver 192.168.0.3

i also made the 953 and 53 port forwarded to my ip through the router

but i still get the servfail with the dig and when i make a nslookup it says cannot find server mydomain.com.mydomain.com SERVFAIL

i've been trying many days now reading as much as i could if anyone can help
Thanks

---

### Post by kyriakos1977 on 2008-02-14
i put in the named.conf.local !!!

it usualy is named.conf
try renaming it and restarting bind

---

