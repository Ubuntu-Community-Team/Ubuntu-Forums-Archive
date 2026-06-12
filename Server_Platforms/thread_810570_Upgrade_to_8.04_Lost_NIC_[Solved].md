---
title: "Upgrade to 8.04 Lost NIC [Solved]"
date: 2008-05-28
forum: Server Platforms
---

### Post by wfx on 2008-05-28
Hi,
if you have more the one NIC in youre server and you miss someone then
check /etc/udev/rules.d/70-persistent-net.rules.
This new udev rules replace the /etc/iftab.
The upgrade process overwrite it and i go in a lot of big troubles.

The converted iftab /etc/udev/rules.d/70-persistent-net.rules:
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:07:95:56:fa:23", ATTR{type}=="1", NAME="eth0"

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:50:bf:76:36:3b", ATTR{type}=="1", NAME="eth1"


# PCI device 0x10ec:0x8029 (ne2k-pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:4f:49:09:85:e8", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

```
This is wrong for me i changed to:
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:4f:49:09:85:e8", ATTR{type}=="1", NAME="eth0"

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:50:bf:76:36:3b", ATTR{type}=="1", NAME="eth1"

```

Now all work perfect for me (not all but most ;-) ).

One interest thing is the eth1 to eth2.
For me it is a bug
and no i dont like to write to the bug tracking system
it is simple ugly organized.

cheers
wfx.

---

