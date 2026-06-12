---
title: "IP Addressing for Multiple Interfaces"
date: 2012-10-01
forum: Server Platforms
---

### Post by jlacroix on 2012-10-01
I recently set up DHCP reservations in my Ubuntu Server-based DHCP server. So far it's working well. However, I have three laptops on the network that will get a reserved DHCP address, and I'm wondering if I can assign the same IP address to the wireless cards and to the integrated wired cards.

My thinking is that this may cause an IP address conflict problem. However, I'd prefer for my laptops to have seamless connections (be reachable by the same IP whether I'm connected via WiFi or wired ethernet).

If I gave the same DHCP reservation to a laptops WiFi and wired Ethernet, would that be a bad thing since it is the same machine?

---

### Post by darkod on 2012-10-01
You can't use the same IP twice on the same network/subnet.

If you make sure the laptop doesn't connect by both wired and wi-fi at any moment, maybe it might work, but I'm not sure. I'm not sure it will even allow you to make reservations to different MACs with the same IP.

And I think it's better not to risk having an IP conflict if one day one laptop connects with both interfaces to the network.

---

### Post by jlacroix on 2012-10-01
> **darkod said:**
> You can't use the same IP twice on the same network/subnet.

If you make sure the laptop doesn't connect by both wired and wi-fi at any moment, maybe it might work, but I'm not sure. I'm not sure it will even allow you to make reservations to different MACs with the same IP.

And I think it's better not to risk having an IP conflict if one day one laptop connects with both interfaces to the network.
Thank you. Is it possible to create something in ~/.ssh/config that would tell ssh to try two different IP addresses so I can still get in to another laptop in my house if it connects to wireless instead?

---

### Post by darkod on 2012-10-01
I don't understand, are you connecting to the laptop or from it?

In both cases, it should work. The SSH server usually runs on all interfaces unless you limit it, so if you have SSH server running on a laptop you should be able to connect to it using both the wired IP and the wi-fi IP.

If you are connecting from the laptop, its IP doesn't really matter unless you are filtering IPs on the SSH server that you are connecting to.

---

### Post by jlacroix on 2012-10-01
> **darkod said:**
> I don't understand, are you connecting to the laptop or from it?

In both cases, it should work. The SSH server usually runs on all interfaces unless you limit it, so if you have SSH server running on a laptop you should be able to connect to it using both the wired IP and the wi-fi IP.

If you are connecting from the laptop, its IP doesn't really matter unless you are filtering IPs on the SSH server that you are connecting to.
Sometimes I connect TO the laptop. If a laptop is setting in another part of the office I may just SSH in and run updates or whatever.

I use an SSH config file so all I have to do is:
ssh <hostname>
And I'm in.

This is possible because in ~/.ssh/config I have something like:

```
Host <hostname>
Hostname 172.16.254.xxx
Port <port number>
User <username>

```

However, if I have two IP addresses on a laptop (one for wired, one for wireless) I wouldn't think I could do ssh <hostname> because it wouldn't know what IP address to find it with.

---

### Post by AMSlider on 2012-10-01
You most certainly can have multiple MACs referencing the same host.  Look at the "hardware ethernet" clause in the "host" config in the dhcpd.conf file and the "fixed_address" clause.  You will have to have a static/fixed address for the laptop.

I have my laptop's wifi and wired eth both using the same reservation inside a tomato based router that uses dnsmasq, which is similar to dhcpd.

---

### Post by jlacroix on 2012-10-01
> **AMSlider said:**
> You most certainly can have multiple MACs referencing the same host.  Look at the "hardware ethernet" clause in the "host" config in the dhcpd.conf file and the "fixed_address" clause.  You will have to have a static/fixed address for the laptop.

I have my laptop's wifi and wired eth both using the same reservation inside a tomato based router that uses dnsmasq, which is similar to dhcpd.
So if I'm understanding correctly, you're saying that I can have the same IP address reference both network cards (contrary to post #2) or are you saying that I have to set it up differently?

---

