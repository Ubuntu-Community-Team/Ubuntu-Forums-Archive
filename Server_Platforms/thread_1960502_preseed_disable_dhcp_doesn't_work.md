---
title: "preseed disable_dhcp doesn't work"
date: 2012-04-17
forum: Server Platforms
---

### Post by vectorz on 2012-04-17
Using a preseed, I cannot figure out how to get the disable_dhcp to work.  I've tried so many variants, passing it to the kernel and specifying in the preseed file, however, it always still tries to grab a lease from a dhcp server.  

I've gotten it to finally use the static assignment only *IF* the dhcp lease fails.  However, as long as there is a working dhcp then it will always try to grab that lease before trying to use static.

Here is what I have (pertinent snip) in my preseed:


d-i netcfg/choose_interface select eth0
d-i netcfg/disable_dhcp boolean true
d-i netcfg/confirm_static boolean true
d-i netcfg/dhcp_timeout string 1
d-i netcfg/dhcp_failed note
d-i netcfg/dhcp_options select Configure network manually
d-i netcfg/get_nameservers string 8.8.8.8
d-i netcfg/get_ipaddress string 10.0.2.20
d-i netcfg/get_netmask string 255.255.255.0
d-i netcfg/get_gateway string 10.0.2.2
d-i netcfg/confirm_static boolean true
d-i netcfg/get_hostname string node1
d-i netcfg/get_domain string mydomain.com

As I had mentioned, I also tried passing the kernel param 'netcfg/disable_dhcp=true' which also had same results.   I've tried many variants such as alleviating the 'dhcp_failed note' and that didn't work either.

Everything else about my preseed is working great.   FTR, I'm injecting the preseed.cfg directly into initrd so it's about as clean and surefire as a preseed can be.

Anyone know what I'm doing wrong?

---

