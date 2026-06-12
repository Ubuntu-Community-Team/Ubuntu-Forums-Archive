---
title: "UFW equivalents of iptables rules?"
date: 2024-02-19
forum: Security
---

### Post by wesbrooks on 2024-02-19
I've been having a fight with iptables and trying to get a computer setup as a router. How would you go about enteringbthe following rules through UFW rather than teying to use iptables directly?

[SIZE=1]iptables -A FORWARD -i eno1 -o wlp6s0 -j ACCEPT 
iptables -A FORWARD -i wlp6s0 -o eno1 -m state --state RELATED,ESTABLISHED -j  
ACCEPT 
iptables -t nat -A POSTROUTING -o wlp6s0 -j MASQUERADE[/SIZE]

---

### Post by TheFu on 2024-02-19
I wouldn't.  

UFW creates IPtables commands and saves them into the /etc/ufw/rules* files.  You can manually add them there in the correct section and they will work.
UFW isn't full featured like iptables is. There are some things the interface just isn't meant to handle.  We are expected to use iptables or nftables to accomplish the more complex things.

NFT is the default in 22.04 and later, I think.

---

### Post by wesbrooks on 2024-02-19
Ok. The backup plan was to completely disable ufw. Looks like I need to read up on NFT.

This is acting as dhcp server, dns server, and gateway from one adaptor on the LAN and another on the WAN.

---

### Post by #&amp;thj^% on 2024-02-19
> **wesbrooks said:**
>  Looks like I need to read up on NFT.
have  a look here for a starting point:[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_and_managing_networking/using-and-configuring-firewalld_configuring-and-managing-networking](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_and_managing_networking/using-and-configuring-firewalld_configuring-and-managing-networking)
> **wesbrooks said:**
> 
This is acting as dhcp server, dns server, and gateway from one adaptor on the LAN and another on the WAN.

The DHCP server isn't a router and can't "direct" traffic to your router. You assign the ip address of your router to the DHCP clients via DHCP but the DHCP server itself has no hand in routing traffic.

Good Luck

---

### Post by Doug S on 2024-02-19
> **1fallen said:**
> The DHCP server isn't a router and can't "direct" traffic to your router. You assign the ip address of your router to the DHCP clients via DHCP but the DHCP server itself has no hand in routing traffic.Yes, but the DHCP server can be on the same box as implements the router.

My main server box is a router/DHCP server/DNS server (internal only)/gateway to/from internet. I use iptables, as I haven't yet converted to NFT. Even though the default is now NFT, the system can still be configured to use iptables.

---

### Post by wesbrooks on 2024-02-20
> **Doug S said:**
> Yes, but the DHCP server can be on the same box as implements the router.


Yup, spot on. This is a former desktop machine with one wifi, two ethernet, and two SFP+ ports connecting to a salvaged Dell Powerconnect 5524 in a small office. I originally used it to connect to the wifi hotspot from my phone and serve that connection to both wired and wireless clients (via wifi router in access mode).

As this is now running behind a comercial 5G modem I'm not hugely concerned about security, but I am doing my best to work to good practice as a slow learning exercise.

Regards iptables I was having a heck of a job trying to clear up persistent saving and hitting permission denied errors on many occations when trying to save to the rules.v4 file.

I'll update with more detail later.

---

### Post by TheFu on 2024-02-20
> **wesbrooks said:**
>  
Regards iptables I was having a heck of a job trying to clear up persistent saving and hitting permission denied errors on many occations when trying to save to the rules.v4 file.

Do you understand UNIX permissions?  Nothing odd there, but on a router it is absolutely critical that those are understood.  On ubuntu (and most UNIX-like OSes), use sudoedit to modify system files.  That's the safe way.

While we can make our own router, there are many details that I fear I'd get wrong, so I use a distro specifically for routing called OPNSense.  It runs on x86-64 hardware and is continuously patched.  It isn't Linux-based.  The way that the pf firewall works is different from how Linux does it. Completely different architecture. [https://opnsense.org/](https://opnsense.org/)  It is a fork of pfSense.

---

