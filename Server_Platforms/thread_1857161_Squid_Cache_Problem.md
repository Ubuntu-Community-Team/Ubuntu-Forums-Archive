---
title: "Squid Cache Problem"
date: 2011-10-09
forum: Server Platforms
---

### Post by husnixs on 2011-10-09
HI all...

after I install Ubuntu server 11.04 and squid Lusca
I follow all instruction of installation...
and it was run...
but after several minute I checked access.log of squid
I found error like this

1318202369.086      0 192.168.0.2 TCP_DENIED/403 2922 GET [http://www.facebook.co](http://www.facebook.co)
m/ - NONE/- text/html
1318202369.350      0 192.168.0.2 TCP_DENIED/403 2922 GET [http://www.facebook.co](http://www.facebook.co)
m/ - NONE/- text/html
1318202370.443      0 192.168.0.2 TCP_DENIED/403 2920 GET [http://maps.google.com](http://maps.google.com)
/ - NONE/- text/html
1318202370.506      0 192.168.0.2 TCP_DENIED/403 2942 GET [http://maps.google.com](http://maps.google.com)
/favicon.ico - NONE/- text/html

the squid won't hit the cache...
but the client still access the internet
I search anywhere on the internet, but still not found the solution...
please anyone of you help me for this issue...

---

### Post by Dangertux on 2011-10-09
Hi :-)

Did you edit the squid.conf file? To include proper ACL's for those you want accessing the proxy?


```

acl local_net src 192.168.1.0/24
http_access allow local_net
http_access allow localhost

```where 192.168.1.0/24 is your local network[FONT=monospace]

Also you might consider adding

```

acl Safe_ports port 80
acl Safe_ports port 443

```

etc...
[/FONT]

---

### Post by Dangertux on 2011-10-10
Bump I saw you asked a similar question on my blog about this. Did this solution work for you? Or is the problem still present, or a different problem?

---

