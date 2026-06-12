---
title: "Static IP's and web hosting"
date: 2011-05-26
forum: Server Platforms
---

### Post by cokacola650 on 2011-05-26
So I've got the standard Ubuntu (not the server version), but I think my question would fall here since I am running apache off of it. I've got Natty Narwhal, with Apache2, behind a Linksys router. I just chance my interfaces config file to make my IP address static and I was wondering do I also need to configure my router to keep my address static? This is just a home project kind of thing, so I'm just using my DSL connection. Is there a way for the company to automatically disallow static IP's or anything? 

Thanks,
cokacola650

---

### Post by arrrghhh on 2011-05-26
> **cokacola650 said:**
> So I've got the standard Ubuntu (not the server version), but I think my question would fall here since I am running apache off of it. I've got Natty Narwhal, with Apache2, behind a Linksys router. I just chance my interfaces config file to make my IP address static and I was wondering do I also need to configure my router to keep my address static? This is just a home project kind of thing, so I'm just using my DSL connection. Is there a way for the company to automatically disallow static IP's or anything?

Your ISP has nothing to do with your LAN.  Don't confuse this with your WAN IP which is handed down by your ISP.

You control your LAN - and so long as you chose a static IP that is **not** within any DHCP ranges on your router/LAN, then the static IP set on the server is all that is needed.  You can put a static entry in your router, but again as long as the IP is outside of any DHCP ranges it's not necessary.

Since you're not running the Server edition, I would prefer that you don't post in this section - this is for 'Server Platforms' after all, not just services running on a Desktop platform :p.  That's just my opinion tho, I'm not a mod ;).

---

### Post by TechSupportx86 on 2011-05-27
For DSL you probably have a dynamic IP, but this doesn't mean you can't host anything.

Just give you server a static LAN IP via /etc/network/interfaces (It will be along the lines of 192.168.1.XXX), Enable DMZ or Static IP to that IP from the router settings, Then forward the appropriate port to that IP (FTP would be 22, HTTP 80, Minecraft 25565, ect).

Now you also need a domain name to get around the dynamic IP. I would recommend DYNdns.com purely on the basis that it's easy, has a linux update client, and it's free.

---

