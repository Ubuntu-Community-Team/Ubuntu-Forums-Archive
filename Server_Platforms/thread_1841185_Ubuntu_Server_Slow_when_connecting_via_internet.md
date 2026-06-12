---
title: "Ubuntu Server Slow when connecting via internet"
date: 2011-09-08
forum: Server Platforms
---

### Post by geidorei on 2011-09-08
Hi

Just setup my first ubuntu server (10.10 stable) - all is well in that SFTP works and very quick, but if i try to access an html page with images etc it either takes ages, or fails to load most of the elements.

Apache installed and is working. Could this be the cause?

Is this normal? My internet speed is 50Mb, upload about 3.5 

Thanks folks. K

NOTE: I lied - ftp is miserable, I was connecting via local IP. doh!

---

### Post by Wayne_V on 2011-09-09
could be any number of misconfigs.

- verify /etc/resolv.conf

- check 'ifconfig -a' and 'route' output

- check 'netstat -s' output

- try to ping you ISPs router and something on the internet

- try to traceroute to your ISPs router and something on the internet

- 'tail -f /var/log/{dmesg,*log}' and watch for net errors

that's just the beginning ....

---

### Post by geidorei on 2011-09-09
Hi

well me being thick - doh again! didnt give it time, ftp doesnt connect.

Right then:
ports open on server, aok
ports open and DMZ on router set
am able to ping internal IP and external IP.
Can see test page if use external IP on browser

However, cant connect via SFTP says could not connect to server.

Any pointers.....

---

