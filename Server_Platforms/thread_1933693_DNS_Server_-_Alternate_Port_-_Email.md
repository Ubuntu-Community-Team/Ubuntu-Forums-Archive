---
title: "DNS Server - Alternate Port - Email"
date: 2012-02-29
forum: Server Platforms
---

### Post by techblvd on 2012-02-29
I just put up a Ubuntu 11.10 LAMP Server.  I am moving 3 websites to it that I currently host on a IIS Server.  

I pay for EasyDNS to forward to my Dynamic IP Address (which never really changes).  I run each site on alternate ports since my ISP blocks port 80.  I also pay for alias email svc for one of my domains that forwards email sent to a mail account I have setup, to a real mailbox.  

I hadn't really considered this until after I put up the Ubuntu server, but, are there services that are configurable within Ubuntu (via Webmin or Virtualmin or other) that would allow me to host my own DNS, forward each site to it's alternate port at my IP address?  Also, can I host my own email creating "actual" mailboxes as opposed to the email forwarding I am currently doing?  Would it be pop mail accounts?  Imapi?  My ISP also blocks port 25, so I would need to host that on an alternate port as well.

I just figured I'd put the question out there.  If these things are all possible, it will save me a couple of hundred bucks a year, so why not :)

---

### Post by efflandt on 2012-03-01
I have done my own DNS locally for a LAN and to cache public names, but you may have difficulty serving public DNS from a dynamic IP, because if your IP did change, nothing in your domain would properly resolve until they could find your nameserver, and the TTL (time to live) expired for other nameservers that have your old IP in their cache.  Although, TTL can be set very short, like 5 minutes instead of weeks.

A specific protocol uses a specific port, and DNS has no provisions for specifying an alternate port.  So if your outgoing port 25 is blocked you would not be able to send mail directly and if incoming 25 is blocked, you would not be able to receive mail directly, unless you were set up to use an incoming or outgoing relay on the internet on a different port (or through a VPN).  There is no real need to split different domains to different ports because a mail server can handle multiple domains, either itself, or as a relay for internel smtp servers on your LAN.  I did that as a test some time ago, with multiple no-ip.com names. The server was set to receive mail for any of the names, kept mail for the main name on the server, and relayed mail for one of the other names to a mail server on my Linux laptop.

So if your port 25 is blocked, you would have to have service set up with somebody elsewhere on the internet to at least relay your mail (if not through your ISP).

---

### Post by techblvd on 2012-03-01
Thanks for that info.  I may just give it a shot for one of my mess around domains

---

