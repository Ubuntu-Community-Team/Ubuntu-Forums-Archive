---
title: "Apache 2 and Ubuntu Server LTS 10.04"
date: 2010-10-04
forum: Server Platforms
---

### Post by devan963 on 2010-10-04
Hello all,

I am unsure if this is an issue with my ISP or my web-server.

If i go to my domain name from an external IP address (My mobile phone) my website loads,

If i go to my domain name from from my home network i.e. laptop > gateway > Webserver it wont load.

Even if i type my external IP address in my browser it wont load(94.*.*.*), if i type in the servers IP directly (local subnet) (192.168.1.11) it works fine, the router is set to redirect all 80,443 requests to my IP to the web-server which it does from external IP's

The reason i wanted to do this is so that i can check my SSL Certs and they will only show me the correct info if i visit the site by domain name

Thanks for any ideas or suggestions!

---

### Post by dtfinch on 2010-10-04
When I've encountered this it's always been a router bug. Some have working loopback on forwarded ports, and some don't. You might want to check if there are any firmware updates available that claim to fix it.

---

### Post by arrrghhh on 2010-10-04
Seems like it would be a good idea to test certs from the WAN anyways...

Just my .02.

---

### Post by devan963 on 2010-10-04
Thanks for the reply,

i think you are right, i have managed to get to it via proxy and through ssh squid proxy so it must be my router

Very annoying but little i can do about it, it is already the newest firmware

May ring Netgear but last time i spoke to them it was as if they didn't know what networking was

---

