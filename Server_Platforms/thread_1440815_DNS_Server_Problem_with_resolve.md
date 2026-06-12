---
title: "DNS Server Problem with resolve"
date: 2010-03-28
forum: Server Platforms
---

### Post by longveasna on 2010-03-28
[B]Client can not resolve with DNS server


  [/B]client can access website with the public IP(like google 72.14.203.98)  for the website but with the name like ([www.google.com](www.google.com)) they can not access.

i see in the /var/log/syslog 


Mar 28 04:29:50 ns1 named[3087]: client 202.58.98.34#1084: query (cache) 'www.google.com.kh/A/IN' denied

so how can i fix about this problem.

Thank for advance

---

### Post by stlsaint on 2010-03-28
your ISP that is hosting your dns server is probably down. You can edit your nameserver config to change the dns servers that are used to a more reliable server. Im not at my machine right now but i think that its in the: /etc/resolv

---

### Post by terazen on 2010-03-30
I'd forward to opendns if you aren't happy with your isp's servers.

---

