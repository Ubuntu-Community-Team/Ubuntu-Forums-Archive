---
title: "dhcpd: address rotating"
date: 2006-06-13
forum: Server Platforms
---

### Post by kentborg on 2006-06-13
My dhcpd is not reusing old IP addresses for any given piece of hardware; each time a client computer or IP phone is rebooted it gets a new IP address.  What would cause this?

Thanks,

-kb

---

### Post by elias@cpaefs.com on 2006-06-13
are you using dnsmsaq? 

check lease time

---

### Post by kentborg on 2006-06-13
I don't think I have dnsmasq anywhere.  Bind 9.3.1 and dhcpd3.

I have played with lease times in /etc/dhcp3/dhcpd.conf, using suggested values from Google searches, and making them longer, but the rotating still happens.  It seems the old lease isn't being found (the file looks readable).

-kb

---

