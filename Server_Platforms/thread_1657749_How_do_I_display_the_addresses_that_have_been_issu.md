---
title: "How do I display the addresses that have been issued by my dhcp3 server?"
date: 2011-01-01
forum: Server Platforms
---

### Post by damateem on 2011-01-01
I want to display the associated host name with each address.

I've found the /var/lib/dhcp3/dhcpd.leases file, but it appears to have an entry for every time a lease was issued so it's hard to tell which ones are currently active.

Thanks,
David

---

### Post by R.Bucky on 2011-01-01
cat /var/lib/dhcp3/dhcpd.leases

---

### Post by damateem on 2011-01-02
Does that mean there's no command to list only the latest address for each host?

---

### Post by SeijiSensei on 2011-01-04
You can "ping-scan" the network with nmap:

nmap -sP 192.168.1.0/24

will return a list of all active machines in 192.168.1.0/24.

---

