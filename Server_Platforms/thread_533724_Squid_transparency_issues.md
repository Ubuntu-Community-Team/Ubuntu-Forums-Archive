---
title: "Squid transparency issues"
date: 2007-08-24
forum: Server Platforms
---

### Post by MCGrunge on 2007-08-24
Hey I work for a company that wants to implement a transparent squid server in order to intercept and forward all non-domain packets to our ISA server for content filtering. So far we have installed squid successfully and made the proxy active, testing this on the squid box itself. Now I am trying to make it transparent so non-domain (employee personal laptops) dont have to be configured. I'm using Squid 2.6 stable 5. All posts I read simply state to add the word transparent after the port listening commands but after I add that and then disable the manual proxy out of Firefox, it seems to bypass the proxy entirely. Any thoughts or suggestions would be of great help!!!

---

### Post by erwall on 2007-08-24
If you don't specify a proxy server in your browser, it's going to attempt to use whatever the default gateway is set to on that box, that's just how it is.  As far as I know, "transparent" actually means 80 gets redirected to 3128 or whatever port squid is on.  Either define the squid box's ip as your default gateway in your dhcp config or specify it in the browser by putting the ip in or make a pac file and specify it in the browser. Then define the default gateway on your squid box to the ip of your ISA box.  Then if possible only allow ISA out port 80 on your firewall.  Good luck.

---

