---
title: "How to setup Apache site config to allow url routing on internal IPs."
date: 2020-08-22
forum: Server Platforms
---

### Post by brian-w-stafford on 2020-08-22
Hi,

I have a home server setup with Apache which hosts a Nextcloud instance that automatically redirects traffic to https. In case it’s important, I have setup a domain name and am using DDNS to route traffic to my server’s dynamic IP. 

Ok, onto my dilemma. 

If I’m using an external IP (ie my phone’s cell service) I can reliably reach my data in Nextcloud using “example.com/nextcloud”  However, if I’m on my home’s WiFi I can only reach it using the internal IP address of the server “192.168.0.2/nextcloud”

This is a hassle because in the Nextcloud app and my browser bookmarks  I have to setup an internal and external connection/account and flip between the two depending on my location in order to get to my data. 

Is there a way to set up the Apache site config to allow https redirect using my domain name regardless of if I’m using an internal or external IP?

Thanks for any assistance here!

---

### Post by TheFu on 2020-08-22
It isn't apache at fault.
You need a dns server for the house that answers the fqdn question with the LAN IP, not the public IP.
BTW, probably a bad idea to have nextcloud directly on the internet.  Setup a VPN so the access is just for you, not the entire world.

For example, internal DNS:
```
$ dig nc.jdpfu.com
; <<>> DiG 9.10.3-P4-Ubuntu <<>> nc.jdpfu.com
;; QUESTION SECTION:
;nc.jdpfu.com.                  IN      A
;; ANSWER SECTION:
nc.jdpfu.com.           2       IN      A       172.22.22.44
;; SERVER: 172.22.22.80#53(172.22.22.80)
```

public DNS:
```
$ dig nc.jdpfu.com
; <<>> DiG 9.16.1-Ubuntu <<>> nc.jdpfu.com
;; QUESTION SECTION:
;nc.jdpfu.com.                  IN      A
;; ANSWER SECTION:
nc.jdpfu.com.           7200    IN      CNAME   jdpfu.com.
jdpfu.com.              3600    IN      A       50.73.91.145
;; SERVER: 1.1.1.1#53(1.1.1.1)

```

If you do the same query for nc.jdpfu.com, you'll get the second answer, but not the first. This is why my Nextcloud server (using Let's Encrypt Certs) works from internal and external locations - though if you attempt to connect from the outside, it shouldn't be allowed. 

For about 5 minutes, every 2.5 months, a connect is allowed from anywhere in the world when I renew the certs for all my domains.  The Let's Encrypt guys changed how they validate connectivity to use at least 3 diverse servers.  This became mandatory last Feb 2020. Prior to that, the failures to connect would just take extra time (about 25 minutes for all our certs), but completed fine.  By allowing world-wide access for those few minutes, renewals for all take about 3 minutes total.  It took me some time to figure out the issue - we use ipset to block thousands of subnets and don't log all the blocked requests by ipset rules.  Just keeping up with non-sensitive information that is fine for world-wide viewing is enough trouble.

Why did I post real IPs?  Because it isn't hard for anyone to get that information already. DNS is public. Internal DNS won't help anyone who can't reach it. Hostnames and website names don't matter either.  

I probably should increase the DNS cache time to at least a day for the public IP. No need to force so many queries to check every hour. All it does is add a load to my DNS provider.  It isn't like the DNS changes here ... it hasn't in about 10 yrs. Static IPs are useful.

Anyway, that's the theory.

---

### Post by volkswagner on 2020-08-22
This is likely a NAT issue with your router. Your router may not allow connections to it's WAN address from inside the LAN. There may be a setting to allow "hairpin NAT". It's been many years, but I forget the name of the setting on consumer grade routers.

---

### Post by kevdog on 2020-08-22
You need a DNS override or NAT reflection on your router to do what you want.  I never knew what these things were until I installed pfsense and used that as my router.  Basically you need to ditch your ****** consumer grade router.

---

### Post by LHammonds on 2020-08-22
> **brian-w-stafford said:**
> This is a hassle because in the Nextcloud app and my browser bookmarks  I have to setup an internal and external connection/account and flip between the two depending on my location in order to get to my data.
Incorrect.  As TheFu has mentioned, you just need your internal DNS to have an entry pointing example.com to your internal IP address of 192.168.0.2.  Your SSL certificate will work just fine regardless of the IP address you use to reach the server so long as you are getting there via the FQDN.  Anything on your LAN using your internal DNS (typically your router) will resolve example.com to 192.168.0.2 and anything outside your LAN "should" resolve your example.com to your external IP which you have configured in the external DNS attached to your domain name.

The NextCloud config allows you to connect via different domain names and IP addresses but forcing SSL prevents you from "allowing" the direct internal IP address to be used (cause the SSL cert check will fail because the IP does not equal the FQDN).  If you cannot figure out how to modify your internal DNS, then or alternative solution would be to configure apache to only force SSL if coming from the outside IP/FQDN and allow non-ssl over the internal IP.

LHammonds

---

### Post by brian-w-stafford on 2020-08-22
@TheFU

Thank you, thank you, thank you!!!

I took your advice and setup a VPN.  You’re right, no sense in leaving my data potentially open to the whole world. Why did I not think of this before?

---

