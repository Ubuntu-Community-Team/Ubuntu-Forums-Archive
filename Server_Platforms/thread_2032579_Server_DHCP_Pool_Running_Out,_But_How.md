---
title: "Server DHCP Pool Running Out, But How?"
date: 2012-07-24
forum: Server Platforms
---

### Post by jlacroix on 2012-07-24
I have a server running Ubuntu Server 12.04 as a DHCP/File server. It runs DNS too but only for local machines. I set it up this way to learn how to do DHCP and DNS, and ended up keeping it as the sole DHCP and DNS provider for my internal network because it ends up being fun.

However, last night was not so fun. My wife has a Roku, and it stopped being able to connect to the network. I spent a few hours troubleshooting it. I figure that it couldn't have run out of DHCP addresses, because I allocated 50 available addresses in the pool. I may have 20 devices using DHCP in my house at the most, and that's an exaggeration. My Static IP devices are all outside the range.

From troubleshooting, I checked the log, and saw that the DHCP server was offering a lease to the Roku's MAC address. The Roku, however, pretended like it couldn't get a connection to the local network. Between having 50 available IP addresses in the pool, the syslog appearing that it is offering a lease to the Roku, and the fact other devices on the network can get an IP address, I blamed the Roku. I told her to toss it and go and buy a new one. She did.

To my dismay, the new Roku had the same exact problem. It couldn't seem to get an IP address. In my frustration, I said "what the heck" and increased the DHCP pool by an additional 5 addresses. The Roku connected immediately.

The entire time, I Googled for the commands I should use to check the number of available addresses, and I couldn't find anything. I was frustrated that the only results I could find where how to set up the DHCP server, not how to administer it.

Worse, I can't think of how 50 addresses could be used up. My wireless router has WPA turned off with a secure randomly generated password that is ridiculous to even type. I have 5 portable gaming consoles that use DHCP, one PS3, two Roku's, and four laptops. My brother in law sometimes brings over his laptop, there's an additional address. Everything else is static, outside the DHCP range.

Here is my current DHCP config:
```
default-lease-time 1209600;
max-lease-time 1209600;
option subnet-mask 255.255.255.0;
option broadcast-address 172.16.254.255;
option routers 172.16.254.1;
option domain-name-servers 172.16.254.5, 172.16.254.1;
option domain-name "localnet";

subnet 172.16.254.0 netmask 255.255.255.0 {
range 172.16.254.195 172.16.254.250;
}

```

---

### Post by SeijiSensei on 2012-07-24
How long a lease time are you using?  If a device connects and gets an address, that address will be held until the lease expires, even if the device never reconnects.

You can see all the leases that the server has allocated in the file [/var/lib/dhcp/dhcpd.leases]("http://manpages.ubuntu.com/manpages/precise/man5/dhcpd.leases.5.html").

I recommend a lease time of no longer than a day.

---

### Post by jlacroix on 2012-07-24
> **SeijiSensei said:**
> How long a lease time are you using?  If a device connects and gets an address, that address will be held until the lease expires, even if the device never reconnects.

You can see all the leases that the server has allocated in the file [/var/lib/dhcp/dhcpd.leases]("http://manpages.ubuntu.com/manpages/precise/man5/dhcpd.leases.5.html").

I recommend a lease time of no longer than a day.
The lease time is in the file above (1209600 seconds, which should be two weeks). In two weeks time I can't think of any reason why I'd have 50 devices connected when I don't own that many.

I checked the leases file you mentioned (thank you SO MUCH for that, I couldn't even find that on Google) and it shows quite a few addresses in there. I counted 29 addresses in there that have an expiration date in the past (one as far back as April). The date and time on the server is correct, so how could that be?

---

