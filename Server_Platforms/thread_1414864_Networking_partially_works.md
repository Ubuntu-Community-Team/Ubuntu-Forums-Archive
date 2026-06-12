---
title: "Networking partially works"
date: 2010-02-24
forum: Server Platforms
---

### Post by chinny on 2010-02-24
Hi everyone. I've got an Ubuntu 8.10 server running in VMware (Esx 3.5) with the Enhanced vmxnet nic.

The VMware tools are installed (I decompressed and compiled) and am able to ping the box by by IP and can also ping internal and external IPs from it (it's got a NAT).

However.....I cannot resolve any DNS entries at all.

The DNS server I'm using is working - have proven that. I've even tried changing to the google public dns server (8.8.8.8) which I can ping fine but I still can't resolve DNS names.
I have Apache and Sshd running - I can get to the ports (tested with nmap) but Apache won't serve pages and ssh won't prompt me for a login. Even connecting directly to the IP rather than to the DNS name doesn't work.
I've removed the original nic and added a new one - re-done the static config for the new nic and get exactly the same. I've even recompiled and re-installed the VMware tools but no joy. Am running out of ideas now....

Does anyone have any suggestions as to what I can try next please as I'm running out of ideas....?


Edit: Have just replaced the nic with the flexible adapter but I get exactly the same.

---

### Post by noway2 on 2010-02-24
Are you using a DHCP server and is it configured to share information with the DNS?  

The most frequency solution I see to this situation is to use a manual hosts table, but this is not an easily extensible solution.  The alternative is to configure the DNS and DHCP to share a common linked key and tell them to automatically update.

---

### Post by chinny on 2010-02-24
> **noway2 said:**
> Are you using a DHCP server and is it configured to share information with the DNS?  

The most frequency solution I see to this situation is to use a manual hosts table, but this is not an easily extensible solution.  The alternative is to configure the DNS and DHCP to share a common linked key and tell them to automatically update.

Hi - it's a static config so no DHCP in the mix.

The hosts file reads:

[I]127.0.0.1   localhost
10.x.x.100  server.domain.com server
::1         localhost ip6-localhost ip6-loopback
fe00::0     ip6-localnet
ff00::0     ip6-mcastprefix
ff02::1     ip6-allnodes
ff02::2     ip6-allrouters
ff02::3     ip6-allhosts[/I]

The resolv.conf reads:

*nameserver 10.x.x.1*

---

