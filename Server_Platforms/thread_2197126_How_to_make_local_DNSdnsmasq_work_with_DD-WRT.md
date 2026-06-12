---
title: "How to make local DNS/dnsmasq work with DD-WRT?"
date: 2014-01-02
forum: Server Platforms
---

### Post by Roasted on 2014-01-02
Hello friends. I have a DD-WRT router running at home with local DNS and dnsmasq running. I can ping/ssh other servers just fine without issue via name, but I cannot ping/ssh by name to a new ubuntu server I just set up *IF* it's on a static IP. I followed an online tutorial and it said to add the entries as such:

auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
network 192.168.1.0
broadcast 255.255.255.0
gateway 192.168.1.1
dns-nameserver 192.168.1.1

Once I made these changes and rebooted I saw in /etc/resolv.conf that 192.168.1.1 auto populated in there, so I figured this was a good sign. Even still, ping/ssh by name does not work. I figured it might just take some time until it would refresh, but 6 hours later, no dice. I set everything back to DHCP and rebooted and ping/ssh via name works fine now.

This is just a little home NAS, so I'm likely just going to set it up with a DHCP reservation anyway, but my inability to get this working had me so curious that I wanted to figure it out regardless of the likely DHCP reservation-based future. What did I do wrong?

---

### Post by CharlesA on 2014-01-02
I just set my server up as a DHCP reservation and it added the entry to DNS. The server is running a static IP, too.

---

### Post by Roasted on 2014-01-03
> **CharlesA said:**
> I just set my server up as a DHCP reservation and it added the entry to DNS. The server is running a static IP, too.

How does your interfaces and resolv.conf file look? Does your ping/ssh by hostname work?

---

### Post by CharlesA on 2014-01-03
> **Roasted said:**
> How does your interfaces and resolv.conf file look? Does your ping/ssh by hostname work?

Yeah, I can ping and use ssh by hostname or IP with no problems.

resolv.conf:

```
search charlesa.net
nameserver 192.168.1.1
```

interfaces:
```
auto lo
iface lo inet loopback
iface eth0 inet manual

auto vmbr0
iface vmbr0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        gateway 192.168.1.1
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0

```

DD-WRT is set up is attached. It's pretty basic.

With that said, the only file that would really matter is resolv.conf and the search directive.

---

