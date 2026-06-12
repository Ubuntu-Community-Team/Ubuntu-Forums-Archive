---
title: "DomainNameServer Bind9"
date: 2015-06-04
forum: Server Platforms
---

### Post by tommy20 on 2015-06-04
Hello all, I am a very newbe for linux.
Tried to setup Bind9 on my Ubuntu 14.02
Server is connected on TL-WR841N Router. (ip address is keep changing when reboot(is it possible to setup to get same ip address such as 192.168.0.101?))
I bought a domain address(ex:tommy.com) from godaddy.com. godaddy.com provide me name server as NSxx.control.com.
Do I need to Setup in the godaddy.com?

Domain is tommy.com
my ip address got from router as 192.168.0.101
nameserver is NS01.control.com, NS02.control.com

Please check what is wrong

[COLOR=#ff0000]/etc/bind/named.conf.local[/COLOR]

zone "tommy.com"{
type master;
file "/etc/bind/db.tommy.com";
};

zone "0.168.192.in-addr.arpa"{
type master;
file "/etc/bind/rev.0.168.192.in-addr.arpa";
};




[COLOR=#ff0000]/etc/bind/db.tommy.com[/COLOR]

tommy.com. 3600 IN SOA ns01.control.com. dns.max.net (
2015060301
28800
7200
604800
600
)
; CNAME Records
email 3600 IN CNAME email.tommy.com
ftp 3600 IN CNAME @
www 3600 IN CNAME @

; MX Records
@ 3600 IN MX 10 mailstore1.tommy.com
@ 3600 IN MX 0 smtp.tommy.com

; NS Records
@ 3600 IN NS ns01.control.com
@ 3600 IN NS ns02.control.com
@ 3600 IN A 192.168.0.101


[COLOR=#ff0000]/etc/bind/rev.0.168.192.in-addr.arpa[/COLOR]

[FONT=arial][COLOR=#007800]$TTL[/COLOR] [COLOR=#000000]10800[/COLOR] ; [COLOR=#000000]3[/COLOR] hours

[COLOR=#000000]**@**[/COLOR] IN SOA ns.tommy.com. NS01,control.com. [COLOR=#7A0874]**(**[/COLOR]
[COLOR=#000000]2011020704[/COLOR] ; Serial - YYYYMMDDNN
[COLOR=#000000]21600[/COLOR] ; Refresh - [COLOR=#000000]6[/COLOR] hours
[COLOR=#000000]3600[/COLOR] ; Retry - [COLOR=#000000]1[/COLOR] hour 
[COLOR=#000000]604800[/COLOR] ; Expire - [COLOR=#000000]1[/COLOR] week
[COLOR=#000000]86400[/COLOR] [COLOR=#7A0874]**)**[/COLOR] ; Minimum - [COLOR=#000000]1[/COLOR] day

[COLOR=#000000]**@**[/COLOR] IN NS ns.tommy.com.
[COLOR=#000000]160[/COLOR] PTR ns.tommy.com.



Do you find problems? Please help. I am digging this problem for little over 3 weeks.

Thank you
[/FONT]

---

### Post by sandyd on 2015-06-04
Few issues i can see
[LIST=1]
[*]To get BIND to work, you need to delegate the domain to BIND. You can do this by removing the default nameservers and seting your DNS servers to point to your public IP Address (see [here]("https://support.godaddy.com/help/article/3952/editing-your-registered-nameservershosts")). You need two of them (i.e. ns1.mydomain.com, ns2.mydomain.com) pointing to your public ip Address
[*]Your bind zone SOA records are wrong. ns01.control.com should be your email and dns.max.net should be your email (with @ replaced by dots).
[*]Your NS records are wrong. They should use ns1.mydomain.com/ns2.mydomain.com (set in #1)
[*]Your A record should refer to your public IP Address if you are looking to host your website at your ip address as well
[/LIST]

I've done some corrections:
```

$ORIGIN tommy.com
@     IN  SOA ns1.tommy.com. dns.max.net (
2015060301
28800
7200
604800
600
)
; CNAME Records
email 3600 IN CNAME email.tommy.com
ftp 3600 IN CNAME @
www 3600 IN CNAME @

; MX Records
@ 3600 IN MX 10 mailstore1.tommy.com
@ 3600 IN MX 0 smtp.tommy.com

; NS Records
@ 3600 IN NS ns1.tommy.com
@ 3600 IN NS ns2.tommy.com
@ 3600 IN A 192.168.0.101


```

---

### Post by tommy20 on 2015-06-05
thank you "Sandyd". I am little confused about router. my server is connedted with a router, so do I need to connect with cable modem or I still can use through router?
I registered my public IP on GoDaddy.com but that ip will change anytime. this is not static IP address. 
Thank you.

---

### Post by sandyd on 2015-06-07
That complicates things a bit...

What you need is a dynamic DNS service like no-ip or afraid.org to keep your public IP updated. You can then use the subdomain that no-ip provides as the nameserver.

About the router - you need to forward UDP/TCP port 53 to your server at home using your router while setting the server to have static DHCP.

---

