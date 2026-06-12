---
title: "ICMP Destination Unreachable Communication Administratively Prohibited"
date: 2008-12-09
forum: Security
---

### Post by Orange Luna on 2008-12-09
I just installed a few security apps and now I'm getting a bunch of these messages:

```
ICMP Destination Unreachable Communication Administratively Prohibited 	2008-12-08 20:23:48 	10.135.32.1 	<my-ip> 	ICMP
```

The source address(10.135.32.1) is the Internet Assigned Numbers Authority so I really doubt that they are attacking me.  This is a pretty severe alert and is causing problems.  Also this problem will sometimes deny web pages opening. What happened.  Can anyone help me figure this out?

---

### Post by bodhi.zazen on 2008-12-09
Dammed security apps :)

What did you install ?

If you know this IP to be trusted, white list it.

---

### Post by Kinstonian on 2008-12-09
It sounds like *backscatter*.  The ICMP traffic you're getting is a response to a stimulus (in this case probably part of reconnaissance).  Your IP could be spoofed similar to nmap's decoy scan.  They are sending packets to IANA or somewhere, spoofed as your IP, which is why you are getting a response out of no where.  At least that's my take on it.

I guess it could be an application you installed sending traffic to IANA, but I don't know what software would do that without you knowing.

**EDIT**

You should also be able to capture the ICMP traffic and look at it in something like Wireshark.  The payload of it should contain *some* of the packet that caused the ICMP response.  Once you understand what is causing that traffic, you are in a better position to determine if it is your computer/network causing it, or if it is really backscatter.

---

### Post by oscar_alfonso on 2009-07-28
All addresses in the 10.0.0.0 range are non-internet routable.  This traffic is not coming from outside.  10.135.32.1 messages are coming from your internal network.  Maybe some node that came to life from your applications.  Have you been able to do a traceroute on this address?

---

### Post by hggdh on 2009-07-28
> **oscar_alfonso said:**
> All addresses in the 10.0.0.0 range are non-internet routable.  This traffic is not coming from outside.  10.135.32.1 messages are coming from your internal network.  Maybe some node that came to life from your applications.  Have you been able to do a traceroute on this address?

Er. Actually, the 10/24 network (and the equivalents from the old class B/C) are *required* to be non-Internet-routable. But... I have seen some network appliances forward them, anyways...

Also, most ISPs will have their routers in a non-routable IP address range.

But you are right, chances are it is from the internal network *or* the ISP.

ICMPs "destination unreachable, communications administratively prohibited" is not common to see nowadays; of old, they would denote services that were made unavailable, and the sysadmins wanted you to know this was not an oversight (as opposed to the more common "destination unreachable", which might, or might not, be an oversight.

Anyway, a lot of implementations now blanket-block ICMP commands/responses on the basis that they are a security risk. Some of them indeed are, and are well-known for that.

---

