---
title: "expand DHCP range"
date: 2013-10-20
forum: Server Platforms
---

### Post by Oso_Rojo on 2013-10-20
I need to expand my DHCP range beyond 255 IP addresses. I'm using this configuration in dhcpd.conf;

```
[FONT=courier new]ddns-update-style none;
authoritative;
default-lease-time 600;
max-lease-time 7200;
Shared-network name {
    option domain-name-servers 10.10.1.2;
[/FONT][FONT=courier new]option routers 10.10.1.2;
[/FONT][FONT=courier new]option domain-name "facingcenter.ipad";
[/FONT][FONT=courier new]subnet 10.10.1.0 netmask 255.255.252.0 {
    [/FONT][FONT=courier new]range 10.10.1.10 10.10.1.254;
[/FONT][FONT=courier new]}
[/FONT][FONT=courier new]subnet 10.10.2.0 netmask 255.255.252.0 {
     [/FONT][FONT=courier new]range 10.10.2.1 10.10.2.254;
[/FONT][FONT=courier new]}
[/FONT][FONT=courier new]}
log-facility local7;
[/FONT]
```(All comments stripped out for brevity.)

I'm getting an error of;
Oct 20 02:21:07 FCServer dhcpd: /etc/dhcp/dhcpd.conf line 31: subnet 10.10.1.0 netmask 255.255.252.0: bad subnet number/mask combination. 
Oct 20 02:21:07 FCServer dhcpd: #011subnet 10.10.1.0 netmask 255.255.252.0 
Oct 20 02:21:07 FCServer dhcpd:                                              ^ 



What do I have wrong here?

Thanks!

---

### Post by tenmoi on 2013-10-20
I think you need to redo a crash course on subnetting:(
(I studied for a CCNA 3-4 years ago so my subnetting skills are rusty, too. But at least I think your range of ip addresses doesn't match the mask) 

Here's my maths:
You've got 2^6 networks and 2^10 host IP addresses. 2^10 divided by 2^6 = 2^4 =64. Minus the network and broadcast you are left with 62 usable host addresses for each subnet. You've allocated to your range 254-10=244 host addresses. Oops! Think again.

Well, that's all that I think I can still remember. :(

---

### Post by Doug S on 2013-10-20
I would suggest this (but I didn't test it):```
ddns-update-style none;
authoritative;
default-lease-time 600;
max-lease-time 7200;
Shared-network name {
    option domain-name-servers 10.10.1.2;
option routers 10.10.1.2;
option domain-name "facingcenter.ipad";
subnet 10.10.[COLOR=#ff0000]0[/COLOR].0 netmask 255.255.252.0 {
    range 10.10.1.10 10.10.2.254;
}
}
log-facility local7;
```

---

### Post by Oso_Rojo on 2013-10-20
Ding, ding, ding, good answer Doug!

I'm surprised how little documentation there is for this on the web. I found very little references to networks with over 254 clients.

Thanks!

---

