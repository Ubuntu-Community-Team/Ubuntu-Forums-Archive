---
title: "How to configure DHCP to check the safety of the client ?"
date: 2014-11-20
forum: Security
---

### Post by ngoctam699 on 2014-11-20
I'm using Unbuntu. As the title, How to configure DHCP to check the safety of the client ? (like NAP on window server)

---

### Post by Lars Noodén on 2014-11-20
Welcome.  Can you go into a little more detail about what you are trying to check and how?  What do you plan to connect to what?

---

### Post by bashiergui on 2014-11-21
See this previous discussion on I presume the exact same topic
[http://ubuntuforums.org/showthread.php?t=2187787](http://ubuntuforums.org/showthread.php?t=2187787)

Are you wanting it only for physically local DHCP assignment? Or do you also have a VPN?

Edit: found a few linux versions of NAP, I've never used tem so I can't vouch for their reliability
[http://blogs.technet.com/b/rhalbheer/archive/2009/01/07/network-access-protection-client-for-mac-and-linux.aspx](http://blogs.technet.com/b/rhalbheer/archive/2009/01/07/network-access-protection-client-for-mac-and-linux.aspx)
[http://blogs.technet.com/b/nap/archive/2008/12/16/nap-clients-for-linux-and-macintosh-are-available.aspx](http://blogs.technet.com/b/nap/archive/2008/12/16/nap-clients-for-linux-and-macintosh-are-available.aspx) (pretty old)

---

### Post by ngoctam699 on 2014-11-21
> **bashiergui said:**
> See this previous discussion on I presume the exact same topic
[http://ubuntuforums.org/showthread.php?t=2187787](http://ubuntuforums.org/showthread.php?t=2187787)

Are you wanting it only for physically local DHCP assignment? Or do you also have a VPN?

Edit: found a few linux versions of NAP, I've never used tem so I can't vouch for their reliability
[http://blogs.technet.com/b/rhalbheer/archive/2009/01/07/network-access-protection-client-for-mac-and-linux.aspx](http://blogs.technet.com/b/rhalbheer/archive/2009/01/07/network-access-protection-client-for-mac-and-linux.aspx)
[http://blogs.technet.com/b/nap/archive/2008/12/16/nap-clients-for-linux-and-macintosh-are-available.aspx](http://blogs.technet.com/b/nap/archive/2008/12/16/nap-clients-for-linux-and-macintosh-are-available.aspx) (pretty old)

Thank you very much! I wan it only for physical local DHCP

I have a Linux DHCP server and windows clients. I want my DHCP server to assign an IP address from a network let's say 10.6.3.0/255.255.255.128 if the client has it's firewall enabled or an IP address from a different network if the client has it's firewall disabled let's say 10.6.3.128/255.255.255.128
It would be much better if I can assign IP addresses from more different networks like if the firewall is enabled 10.6.3.0/255.255.255.0, and if it is disabled 10.6.4.0/255.255.255.0

---

