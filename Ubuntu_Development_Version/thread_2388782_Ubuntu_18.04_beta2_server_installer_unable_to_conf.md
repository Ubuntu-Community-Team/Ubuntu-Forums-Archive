---
title: "Ubuntu 18.04 beta2 server installer unable to config network on 16.04 kvm host"
date: 2018-04-07
forum: Ubuntu Development Version
---

### Post by luzi822 on 2018-04-07
I am trying to install Ubuntu 18.04 server on Ubuntu 16.04 kvm host.
I am using ubuntu-18.04-beta2-live-server-amd64.iso

1. At text mode, "Timed out waiting for device dev-disk-by...device." "Dependency failed for /subiquity_config." warnings appear.
2. Installer pause at "A start job is running for Wait for Network to be Configured" for nearly 2 mins.
3. In "Network connection", the progress bar stop at 66%, and then show a "Network configuration timed out; please verify your settings".  In network setting I use "Used DHCPv4 on this interface" and "Do not use (IPv6)".  In fact, my ISP does not support IPv6.  Anyway, the installer does not work here.

More information:

- Tried fresh install 17.04, everything run nice.
- Tried fresh install 17.10, the installer run ok.  However after installation, it show "A start job is running for Wait for Network to be Configured" for a long time when boot, and unable to connect to network after that.
- Tried fresh install 17.04, then upgrade to 17.10.  Everything seems perfect.  No warning, no pause, able to connect to network.

I guess that is the problem of netplan, but I am not sure.

---

### Post by luzi822 on 2018-04-07
I have just discover ubuntu-18.04-beta2-server-amd64.iso and install 18.04 successfully.
However, after installation, the system is still unable to connect to network.
Then I try remove netplan and install ifupdown, then my system works.
So I quite sure the problem come from netplan.

---

