---
title: "Ubuntu Server 16.04 Generates a Different IPv6 DUID on Every Reboot"
date: 2018-06-03
forum: Server Platforms
---

### Post by sirwobbythefirst on 2018-06-03
Hey everyone,

I'm having an issue with my Ubuntu Server 16.04 LTS virtual machine where the OS seems to generate a different DUID for IPv6 on each restart, I have IPv6 setup and working for my network and Ubuntu pulls an IPv6 address and is able to use that address but the IP address it grabs changes because of the DUID used, when I check on the DHCP Management console in Windows, there are about 2-3 extra IP addresses generated.

This is incredibly frustrating and I haven't been able to find any information on why Ubuntu does this or how I can go about getting it to generate a more stable DUID such as the Type 4 DUID and for this virtual machine I have a DHCPv6 reservation and every other device on the network that supports IPv6 and doesn't specifically need a static IPv6 address (e.g. DHCP and DNS themselves or my router) persist their DUIDs and thus grab the same IPv6 address each time but Ubuntu doesn't.

Does anyone have any ideas on how I can gain a more stable DUID as well as why Ubuntu does this? I understand there are multiple DUID types and it looks like Ubuntu uses the Type 1 variant which is Link-Local + Timestamp.

---

