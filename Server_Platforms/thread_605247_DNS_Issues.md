---
title: "DNS Issues"
date: 2007-11-06
forum: Server Platforms
---

### Post by godsfshrmn on 2007-11-06
I am trying to add a domain to my home server, but I can't get the name server to work right. When I try to ping (ns1.wow-sig.com) I get an error. I am using Webmin to setup the DNS server.
Config file
```
$TTL        86400
@       IN      SOA     ns1.wow-sig.com. admin.wow-sig.com. (
                        2007110601       ; serial, todays date + todays serial #
                        28800              ; refresh, seconds
                        7200              ; retry, seconds
                        604800              ; expire, seconds
                        86400 )            ; minimum, seconds
;
                NS      ns1.wow-sig.com.              ; Inet Address of name server 1
                NS      ns2.wow-sig.com.              ; Inet Address of name server 2
;

  MX      10 www.eqsig.com.

wow-sig.com.      A        192.168.1.5
www       A       192.168.1.5

wow-sig.com.       TXT  "v=spf1 a mx ptr ~all"

```

Godaddy will not let me add these name servers because they do not exist I presume. Is my IP address not supposed to be entered anywhere?

---

### Post by HermanAB on 2007-11-06
Hmmm, I'm a little rusty, but this should be better:

$TTL        86400
@       IN      SOA     ns1.wow-sig.com. admin.wow-sig.com. (
                        2007110602       ; serial, todays date + todays serial #
                        28800              ; refresh, seconds
                        7200              ; retry, seconds
                        604800              ; expire, seconds
                        86400 )            ; minimum, seconds

wow-sig.com.  IN  NS      ns1.wow-sig.com.
wow-sig.com.  IN  NS      ns2.wow-sig.com.

wow-sig.com.  IN  MX      10 [www.eqsig.com](www.eqsig.com).

wow-sig.com.            IN   A        192.168.1.5
[www.wow-sig.com](www.wow-sig.com).   IN  A       192.168.1.5

wow-sig.com.       TXT  "v=spf1 a mx ptr ~all"

---

### Post by godsfshrmn on 2007-11-06
Yay I have it working so far. My ISP blocks port 80 and I have my server running on 8080. I can't have people going to the domain from site.com:8080 so how do I re route it to work with just site.com?
edit: nevermind :D

---

