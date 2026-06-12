---
title: "Server DNS Setup"
date: 2013-08-09
forum: Server Platforms
---

### Post by Brandon_Cunningham on 2013-08-09
Hey there, its been a long time since i dabbled in linux server but, i am trying to setup my server as a DNS. Things to note i have bind and webmin installed and working, but for the life of me i cant get my zones to work. I know the DNS is now up and working. Below is some of my files. This ip fake but for display purposes the rest should be all correct.
Thanks in advance for any assistance.

> #named.conf.local
#FORWARD LOOKUP ZONES - Holds A records, maps hostsnames to IP's
zone "webpraxgaming.net"
{
type master;
file "/etc/bind/zones/webpraxgaming.net.db";
};
#REVERSE LOOKUP ZONE - Holds Pointer records, maps IP address to a hostname
#208.229.144.129
zone "0.229.208.in-addr.arpa"
{
type master;
file "/etc/bind/zones/rev.0.229.208.in-addr.arpa";
};



Below in whats in my zones folder
> 


$TTL 3D
@ IN SOA ns1.webpraxgaming.net. ns2.webpraxgaming.net. admin.webpraxgaming.net. (
20130808;
28800;
3600;
604800;
38400
);






webpraxgaming.net. IN NS ns1.webpraxgaming.net.
webpraxgaming.net. IN NS ns2.webpraxgaming.net.
IN A 208.229.144.129
webpraxgaming IN A 208.229.144.129
www IN CNAME webpraxgaming
webpraxgaming.net. IN A 208.229.144.129
ns1 IN A 208.229.144.129
ns2 IN A 208.229.144.129





below is the revers zone file
> 
$TTL 3D
@ IN SOA ns1.webpraxgaming.net. ns2.webpraxgaming.net. (
20130808 ;
28800;
86400;
604800;
86400 )


IN NS ns1.webpraxgaming.net.
IN NS ns2.webpraxgaming.net.
129 IN PTR [www.webpraxgaming.net]("http://www.webpraxgaming.net/").
129 IN PTR webpraxgaming.webpraxgaming.net.





When i do a dig of webpraxgaming.net i get the below
> 


; <<>> DiG 9.8.1-P1 <<>> webpraxgaming.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 9982
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;webpraxgaming.net. IN A


;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Aug 9 08:57:27 2013
;; MSG SIZE rcvd: 35


---

### Post by Brandon_Cunningham on 2013-08-09
so i think i solved it, my serial number in local.db was at 2 so i changed my zones to 2 and i think its working now

---

### Post by Profark on 2013-08-10
Check this it will help you
[http://http://ubuntuforums.org/showthread.php?t=2166260]("http://http://ubuntuforums.org/showthread.php?t=2166260")
Second you are not suppose to write this
webpraxgaming IN A 208.229.144.129
Instead
Www in cname ns1
Your reverse zone will also not work ip reversing is wrong I think what is your subnet mask if
255.255.255.0 then 144.229.208.in-addr.arpa 
Or if
255.255.0.0 then 229.208.in-addr.arpa

---

