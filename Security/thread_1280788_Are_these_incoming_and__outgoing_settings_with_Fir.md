---
title: "Are these incoming and  outgoing settings with Firestarter reasonably safe?"
date: 2009-10-02
forum: Security
---

### Post by mikodo on 2009-10-02
Newbie questions:

1.) I was going to show through screenshots, my incoming and outgoing configurations of Firestarter but found that this is not allowed so, please comment on the second question.

2.) Would having a router like a Linksys [www.linksysbycisco.com/US/en/support/BEFSR41](www.linksysbycisco.com/US/en/support/BEFSR41) provide an enhanced level of security by placing it between the ISP's modem and my one computer. (I believe it just provides NAT in it's security functions). I already use Firestarter configurations for inbound and outbound connections.

Thank you

---

### Post by Nepherte on 2009-10-02
Screenshots?

---

### Post by mikodo on 2009-10-02
> **Nepherte said:**
> Screenshots?
 I was not allowed to reproduce the screenshots like I thought I would be able to. Sorry.

---

### Post by ikt on 2009-10-02
what are you trying to protect?

---

### Post by mikodo on 2009-10-02
> **ikt said:**
> what are you trying to protect?

Just intruders from entering my computer. I am careful in my computer/browsing usage, just worry about security. Oh yes, I just use Ubuntu Hardy as OS and nothing else on my home computer.

---

### Post by cdenley on 2009-10-02
If you have a NAT router between your computer and the internet, then connections to your computer cannot be established over the internet even if you run a server, unless you configure port-forwarding or a DMZ. Even if you didn't have a NAT router between you and the internet, they still wouldn't be able to establish a connection to you unless you installed a server to accept their connection.

Simply don't install servers, then you don't need a firewall.

---

### Post by xpod on 2009-10-02
> **mikodo said:**
> Newbie questions:

1.) I was going to show through screenshots, my incoming and outgoing configurations of Firestarter but found that this is not allowed so, please comment on the second question.

2.) Would having a router like a Linksys [www.linksysbycisco.com/US/en/support/BEFSR41](www.linksysbycisco.com/US/en/support/BEFSR41) provide an enhanced level of security by placing it between the ISP's modem and my one computer. (I believe it just provides NAT in it's security functions). I already use Firestarter configurations for inbound and outbound connections.

Thank you

I`d get rid of firestarter and just use the router as you planned.
I used firestarter myself for quite a while although i needed simple ICS configuration and firestarter was just the easiest method for me at the time.
It can scare a lot of people with it`s *blocked* connections function and although i never had any issues with it the general advice around here now is to use the UFW/GUFW configuration tool instead, if you *really* need to that is.As the previous poster mentioned though you dont need to be configuring firewalls if you dont plan on opening any ports and running all kinds of services/servers etc.
I`ve used our Linksys/Netgear routers for a couple of years now so firestarter and the like are completely pointless.

---

### Post by cariboo on 2009-10-03
+1 for a router, don't forward any ports, and make sure remote access is turned off. Use a strong password for the administration interface too.

---

