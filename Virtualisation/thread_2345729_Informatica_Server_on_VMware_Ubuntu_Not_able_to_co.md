---
title: "Informatica Server on VMware Ubuntu: Not able to connect"
date: 2016-12-07
forum: Virtualisation
---

### Post by 1919teja on 2016-12-07
Hi,
I successfully installed Informatica server on VMware Ubuntu and also installed Informatica client on Windows 10.I am not able to connect to Informatica Server or Ping from Windows 10 Command Prompt.(CMD).
These are my Steps:
1. VMware network setting is NAT.
2. Ubuntu Linux IP (ifconfig) on Windows Host file.
3. When I tried to ping from Windows 10 CMD ,it gave me REQUESTED TIME OUT message.
4. I tried to connect with PUTTY but no luck. (I disabled Firewall on Windows 10 & on UBUNTU and also Installed sshopensever on Ubuntu)
Can anyone have any suggestion?
Thanks

---

### Post by howefield on 2016-12-07
Thread moved to the "*Virtualisation*" forum.

---

### Post by KillerKelvUK on 2016-12-08
Unless you have some specialised routing occuring within your VMware host I don't believe your network configuration will support what you are trying to achieve.  With your guest vm having its network configured for NAT that means it is sharing the hosts IP address, this allows it to connect outwards e.g. to a website but doesn't allow a remote/external source to connect inbound to the guest vm.  You need to change the guest configuration to use something like a network bridge where the guest has its own IP address that is unique in the subnet aka not the same as the host.  VMWare will have a 'bridge' network option somewhere but I've never used it so can't advise further.

---

