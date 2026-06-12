---
title: "Domain Host resets"
date: 2007-05-16
forum: Server Platforms
---

### Post by favero on 2007-05-16
Under Administration->Network->General I change the Hostname to my hostname and my domain to my domain... but after rebooting the domain is blank.

---

### Post by jonallport on 2007-05-16
The domain name is held in /etc/resolv.conf in the form

domain mydomain.net

Set the domain name via Adm/Net/Gen and cat /etc/resolv.conf to see this.

Sounds like you are using DHCP to allocate ip addresses and your DHCP server doesn't set the domain, this value will be lost when dhclient makes a new /etc/resolv.conf at allocation.

2 ways to resolve this:

1 - (The proper way) Reconfigure your DHCP server to issue domain with ip address
2 - (The dirty method) Add 'echo domain mydomain.net >>/etc/resolv.conf' to /etc/init.d/rc.local, this will append the domain value to the file at boot irrespective of DHCP config.

---

