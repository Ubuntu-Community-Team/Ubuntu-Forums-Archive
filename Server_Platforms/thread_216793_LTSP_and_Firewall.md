---
title: "LTSP and Firewall"
date: 2006-07-16
forum: Server Platforms
---

### Post by cesera on 2006-07-16
I am trying to run LTSP on my kubuntu box, I have managed to install it, but it is still not working. I suspect that might be caused by my firewall. I use guarddog to administer the firewall and by default it is very restrictive. Can anyone tell me what ports (TCP and/or UDP) I need to open up for LTSP to work properly?
 
Thank you very much

---

### Post by JoeGregory on 2008-01-02
Hi,

This is from a reply I get on the ltsp-discuss mailing list.

If you're on a private secured subnet, try to turn off firewall or limit
allowed ltsp client subnet to access the server,
or make sure these ports (both tcp and udp) are accessible by the subnet
where ltsp client resides, 22 (ssh), 941 (nfs), 111 (portmap), 53
(dns), 3128 (squid), 7100 (xfs), 514 (syslog), 67 (dhcp), 69 (tftp),

1.5 years later, but maybe better than never :)

---

