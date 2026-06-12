---
title: "Sun Fire x4100 Network Interface Issues During Install"
date: 2008-07-07
forum: Server Platforms
---

### Post by questionlp on 2008-07-07
When attempting to install either Ubuntu 7.10 or 8.04 LTS (x86 and amd64 versions) on a Sun Fire x4100 with the latest ILOM and firmware version, I am unable to get any of the four integrated "Intel Corporation 82546EB Gigabit Ethernet Controller(s)" configured.

The link light on all four ports come up while the server is booting and up through to the "Configure the network" screen where it lists the four interfaces. At that point, the link for port 0 goes down and selecting that port drops me to the "Ubuntu installer main menu" screen. The problem repeats itself for the other three interfaces and ports. Looking at the virtual screen with the messages, I see:

netcfg[xxxx]: INFO: eth0 is disconnected. (MII)
netcfg[xxxx]: INFO: eth0 is not a wireless interface. Continuing.
netcfg[xxxx]: INFO: eth1 is disconnected. (MII)
netcfg[xxxx]: INFO: eth1 is not a wireless interface. Continuing.
netcfg[xxxx]: INFO: eth2 is disconnected. (MII)
netcfg[xxxx]: INFO: eth2 is not a wireless interface. Continuing.
netcfg[xxxx]: INFO: eth3 is disconnected. (MII)
netcfg[xxxx]: INFO: eth3 is not a wireless interface. Continuing.
main-menu[xxxx]: Menu item 'netcfg' succeeded but requested to be left unconfigured.

I validated that the four network links are good when used with other servers (no MAC filtering or switch port security used on the switches). The issue also does not rear its head when installing Debian 4.0r3. I would prefer to stick with the set company standards of Ubuntu 7.10 or 8.04 LTS.

I searched Google and several other sites but didn't see any other posts or messages regarding this issue.

Anyone run into this problem or have any suggestions? Thanks.

---

### Post by kpostrup on 2009-10-23
Hello,

I know this is an old thread. However as no one has replied, I will.


I am experiencing the exact same problem on a Sun Fire X4170, also with latest ILOM firmware and BIOS. I am however having this problem on Debian 5.0 installations.

However this problem does not occur in Ubuntu 9.04 installations.

If I configure the eth0 interface manually, it works fine.

Did you find any solution for this problem?

---

