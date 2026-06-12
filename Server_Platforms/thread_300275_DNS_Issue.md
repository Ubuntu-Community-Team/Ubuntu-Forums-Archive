---
title: "DNS Issue"
date: 2006-11-15
forum: Server Platforms
---

### Post by bloodniece on 2006-11-15
Hi, I have a domain registered through No-IP.org and I have the Linux client installed on my Edgy server.  Everything was working fine till today.

Overview:
[LIST]
NAT set on Linksys router forwarding 80 and 53 to local server static IP
No-IP linux client installed as a runlevel service in init.d (client is running)
Local computers on my local subnet can access the server using the FQDN
Remote users in the WAN cannot access my server using FQDN or direct IP.
I can access the router's admin page using the [http://mydomain.com:8080](http://mydomain.com:8080) from the WAN.
[/LIST]

This has been a real head scratcher for me.


Any insight is welcome and needed.

thanks

---

### Post by skymt on 2006-11-15
Can your machine be pinged by hostname from the WAN? If so, the problem is likely with port forwarding, not DNS.

---

### Post by bloodniece on 2006-11-15
> **skymt said:**
> Can your machine be pinged by hostname from the WAN? If so, the problem is likely with port forwarding, not DNS.

Yeah, I can ping from the WAN.  I'm double-checking the NAT.  I might go DMZ and see if that works.

---

### Post by bloodniece on 2006-11-15
> **bloodniece said:**
> Yeah, I can ping from the WAN.  I'm double-checking the NAT.  I might go DMZ and see if that works.


Ok, I deleted the NAT redirect rule for port 80 and recreated it and now it works.  Not sure why that worked, especially since the rule I recreated was exactly the same as it was before.  Thanks!

---

