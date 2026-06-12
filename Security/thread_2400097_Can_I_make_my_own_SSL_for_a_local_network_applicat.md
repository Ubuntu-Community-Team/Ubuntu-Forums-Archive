---
title: "Can I make my own SSL for a local network application?"
date: 2018-09-02
forum: Security
---

### Post by webmiester on 2018-09-02
Hi everyone,

Can I make my own SSL certificates that my company's computers can use when communicating with the company server?

Can I just make one instead of having to purchase it?

---

### Post by TheFu on 2018-09-02
Yes, you can. There is an easyCA tool.

Actually, I moved from self-signed certs to Let's Encrypt free certs because using self-signed certs doesn't provide the same security as a 3rd party cert to prevent MiTM attacks.

---

### Post by webmiester on 2018-09-02
Cool.  I am reading on the Let's Encrypt free certs, SSLforFree says it only works for domain names and not for IP addresses.  So I might not be able to make one for my local server.  Yeah, but preventing MiTM attacks would be nice.

---

### Post by TheFu on 2018-09-02
There are trade-offs using a public CA or a private CA or self-signed certs. Each has security implications.

With a public CA like Let's Encrypt, you need to have a domain AND you need to allow the website to be available for 5 minutes every 90 days to allow the LE certification process to work.  But you don't need to modify any clients, since LE is already in the list of approved CAs on all clients.  Let's Encrypt will not generate certs for non-registered domains or for non-public IPs.
I run a few private websites that normally can only be reached by using a VPN on a server LAN, but to make clients have easy access, using HTTPS, I deploy LE certs onto those systems. That means having to open the router port forward for selected public IPs to those internal IPs for 5min every 90 days.   LE certs are limited to 90 days.

If you use a private CA, then you have to modify every client to include your private CA "server cert".  That can be a hassle or next to impossible for systems like locked smart phones or tablets. Fortune 50 companies do this so they can MiTM all web traffic on their network and MiTM all HTTPS traffic going onto the internet to scan the traffic for any issues.  It also means that whenever employees on the internal network are checking their bank or brokerage or retirement accounts, the corporation can see all that traffic. Nothing is hidden and if the enterprise cert isn't on a machine, then the external access should be blocked.

If you use a self-signed cert, then clients will get a nasty warning that they are connecting to an non-secure site every time.  Some browsers will refuse to go forward to the site.  If you setup the web server to use the most secure SSL settings, this will block self-signed certs and expired certs of any sort. I don't recall which browsers refuse, but I think chrome is one.

Or you can pay a public CA $40-$400/yr for a cert and use whatever whatever domain/IP validation you like. They will usually make certs for non-public IPs. They don't care.  You can buy 5 yr certs so the maintenance doesn't happen all the time.  There are good and bad things about doing that.  The more often you have to deal with certs and CAs, the better you get at it.

So you have to decide which of the choices are best.  Hopefully someone else will clarify anything that isn't clear or slightly off with any of the stuff above.

---

