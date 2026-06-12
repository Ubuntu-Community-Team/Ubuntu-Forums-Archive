---
title: "Question on DNSMasq"
date: 2005-11-01
forum: Server Platforms
---

### Post by WebsterTrivium on 2005-11-01
Okay, I got DNSMasq configured and working, and I get name resolution for all my windows boxes. I figured out why the the DNS/DHCP server was returning 127.0.0.1 (It was listed in hosts file. Ubuntu maps it's name to itself. Without this, sudo stops working. It uses gethostbyname(), which requires the mapping in the host file. I replaced it with the static IP address I assigned to my DNS/DHCP server in the hosts file, and it still worked, and now returns the right address when pinging it, and sudo still works.)

Now, I've got two windows boxes that are working correctly, they can get out on the WAN and ping by name for each other and the DNS/DHCP server. I can do an ipconfig /all on my windows machine and see the connection specific DNS suffix as my domain I setup on the DNS/DHCP server. DNS/DHCP are pointed correctly, and everything else looks right. I'm new to linux, is there something similar I can do to get the same details? I did ifconfig -a, but it does not have the same level of detail.

I brought up a second Ubuntu 5.10 box. It can ping the fileserver, and the two windows boxes by name, but none of these boxes can ping that second Ubuntu box.

Any ideas why this might be? Any suggestions or thoughts are appreciated!

/etc/dnsmasq.conf:
```
# Never forward plain names (with a dot or domain part)
domain-needed
# Never forward addresses in the non-routed address spaces.
bogus-priv

# Uncomment this to filter useless windows-originated DNS requests
# which can trigger dial-on-demand links needlessly.
filterwin2k

# set range of valid addressed for DHCP server
dhcp-range=192.168.10.200,192.168.10.225,12h

#DNS Connection specific domain
expand-hosts
domain=test.com

# default gateway
dhcp-option=3,192.168.10.1
```

---

