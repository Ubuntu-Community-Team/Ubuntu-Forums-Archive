---
title: "DHCP Client not working during install with a W2k3 DHCP server that gives 2 gateways"
date: 2008-12-16
forum: Server Platforms
---

### Post by iest on 2008-12-16
Hi,

This is my first post in the forums, so hi everybody.

I have recently got a Dell Virtualization Server, where we have installed the now free VMWare ESXi Hypervisor. Testing it, I decided to create one VM with Ubuntu Server, mainly to have a test LAMP enviorment.

Our network is mainly Microsoft Based, including DNS Server, DHCP, WINS, etc. The DHCP Server is configured to assign to clients an IP, DNS address, WINS Address and TWO Gateway Addresses.

When starting the install of Ubuntu Server Intrepid, the DHCP config fails. Not only that, but the DHCP scope in the server fills with "BAD_ADDRESS" entries (Nice DOS :)). After confirming with Wireshark that the DHCP Client was declining every lease, I looked at the Intrepid Installation Syslog in order to find out why.

After every DHCPACK received, it showed two errors. I couldn't copy/paste from the vm, so I'll transcript them as well as I can:

```
(Date Here) main-menu[2758]: (process:11043): ip: RTNETLINK answers: File exists
(Date Here) main-menu[2758]: (process:11043): dhclient.c(2138): null pointer
```

After looking for the error in google, seemed like something routing related, so I created a custom lease for the VM MAC Address with only one Gateway address. Now the DHCPClient works just fine during install.

My question is, Can someone suggest a better fix? Should I fill a bug report? I'm reluctant as I have only replicated it in VMWare ESXi and VMWare Workstation, and maybe the issue is related to the virtual adapters only.

Also, as I had a hard time figuring it out, wanted to put it online in case other people encounters this issue (And sorry if it's duplicated... I haven't find anything related in the forums).

Thanks in advance!

(Please excuse my mildly broken english :))

Jail Benedict

---

