---
title: "dhcpd allow only certain hardware vendors"
date: 2008-10-11
forum: Server Platforms
---

### Post by hatfieldd on 2008-10-11
I need to configure a dhcp server to only give leases if a request comes from an allowed hardware vendor.

The dhcpd.conf is already set with multiple classes, determined by 
option vendor-class-identifier="XXXXXXXX") etc. to give specific options to the client.

does the 'deny unknown-clients' options work with classes or only the hosts specified by their full HW addresses?

I have read the man pages for dhcpd, but could not find a clear definition of what qualifies as a known host, in regards to the allow/deny unknown-hosts option.

I appreciate any help or advice, I would also be open to suggestions to allowing only certain OUIs to boot if anyone could guide me how to specify that in the dhcpd.conf file.

Thanks.

---

