---
title: "DNS - Moving beyond forward and mask"
date: 2010-10-21
forum: Server Platforms
---

### Post by jpinkham on 2010-10-21
I have a business class static IP service and my ubuntu server is hosting my dynamic pages using Tomcat6 and MySQL just fine.

I've got my static IP 192.168.1.120 setup OK, got Tomcat6 serving port80 (that was fun), and I've got my LinkSys firewall passing port 80 thru.

Now, in GoDaddy, if I "forward" to my external IP, users address bar gets changed to:

[http://123.45.67.89/whateverPage](http://123.45.67.89/whateverPage)  --  This is bad.

I've been temporarily solving this issue using their "Forward and Mask" feature, but that makes everything an IFrame which has various drawbacks I don't like.

My domain currently uses GoDaddy's nameservers.  The A record is set to my numeric IP, and there is a CNAME for www  set to @  which is probably just means whatever the A says.

I see various help pages discussing HOW to setup a bind service to run my own nameserver, which I can figure out how to have godaddy point to.

I guess I don't understand the higher level WHY of nameservers - is this even what I want to be doing?  Isn't there some easier way to use Godaddy's (or my ISP's or someone else's?) nameserver?  Unless I can just set it and forget it somehow, I'm not sure I want to run a bind service myself - I just want users to see my domain name in their address bar.  Is this the path in that direction? What am I missing?  Can my LinkSys router do it for me?

I've also seen discussion of DynDNS, which seems close to what I need, except I've got a permananet business class ISP static IP so I don't need the main thing they seem to offer.

If it helps, I've got this:
 /etc/hosts
127.0.0.1 localhost
127.0.1.1 myhost
192.168.1.120 myhost.mypublicdomain.com mypublicdomain.com

and /etc/resolv.conf
search mypublicdomain.com
nameserver 192.168.1.1             <-- my linksys router which is also my DNS server

---

### Post by jpinkham on 2010-10-21
OK, that didn't take long to answer my own question - hope this helps someone else.

What I hadn't noticed was that the A record was set to another IP address besides mine - when I tracert it I get a name like pwfwd-v01....secureserver.net.

Of course, that's how GoDaddy is implementing the 'forward' feature.  So if I just change the A record to my own IP, then badda boom badda bing - it works fine!

Geesh.  Can't blame em for wanting to sell hosting so they don't make that concept more clear, but my fault for not looking close enough at that A record.

Anyway, hope someone else learned something from that.
-- Jim.

---

