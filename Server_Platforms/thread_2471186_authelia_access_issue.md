---
title: "authelia access issue"
date: 2022-01-22
forum: Server Platforms
---

### Post by sniper8752 on 2022-01-22
I recently stood up my own internal server.  I attempted to access the domains, and the browser just says "trouble finding that site".  When I access the IP, it asks me to accept the self signed cert to continue, and when I do, I am taken to a '404 page not found' page.  In my local machine, I've modified the hosts file to point all three domains to the IP address of the authelia instance.  How can I resolve this?

---

### Post by TheFu on 2022-01-22
> **sniper8752 said:**
> I recently stood up my own internal server.  I attempted to access the domains, and the browser just says "trouble finding that site".  When I access the IP, it asks me to accept the self signed cert to continue, and when I do, I am taken to a '404 page not found' page.  In my local machine, I've modified the hosts file to point all three domains to the IP address of the authelia instance.  How can I resolve this?

Many "modern" browsers are protecting people like you and I from ourselves.  They ignore the system settings and only use DNS. A few years ago, Google's junk would only use Google's DNS ... they were protecting us from ourselves.

If you are running an internal website, the easiest, long-term, answer is to run an internal DNS and point all your systems at it. You could make that DNS server a PiHole or just run the software inside any container or VM if you don't want to dedicate a Pi to it.  It is better for security if DNS does NOT run on a router. Same for DHCP. There are multiple DNS and DHCP attacks against WAN-routers running those services.

I posted how to bring up a pi-hole + DNS in these forums in an LXD container either 1 or 2 yrs ago. I don't recall.  It was surprisingly simple.  The key is that the DNS needs to be available for all your systems 24/7/365, so having a quick backup DNS (or having the LXD cloned to a different physical system (2 DNS is always a good idea) will make your life easier too ... er ... eventually.

BTW, probably don't want to use self-signed certs these days.  Use Let's Encrypt certs. You only need to allow access to the website for the 90 seconds that the cert is requested every 80 days or so. Set a calendar reminder, since they expire every 90 days and if something bad happens, you'll want a few days to address it. I renew every 77 days ... that way it is always the same day of the week when I renew and I know there will be time to do it.  I have to drop my firewalls for most of the world for this short period of time. The Let's Encrypt team really thinks that everyone, everywhere, so have access, so they test from 3+ different continents that the website can be accessed. For the first few years, it worked when only one location could access the website, but then they made it mandatory and refuse to issue/reissue certs if the site cannot be accessed by their random check locations.
Also, by allowing LE access from anywhere during a re-issue, there aren't timeouts, so the time to get the re-issued certs is relatively quick. I think is it 90 seconds for my 20 certs, when it was over 12 minutes when I was blocking places known to be unfriendly.

---

