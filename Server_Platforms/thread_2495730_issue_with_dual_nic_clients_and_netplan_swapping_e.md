---
title: "issue with dual nic clients and netplan swapping ethernet interfaces"
date: 2024-02-28
forum: Server Platforms
---

### Post by hckrmagoo on 2024-02-28
[COLOR=#0C0D0E][FONT=-apple-system]Background: 1500+ stations running Ubuntu Server + ubuntu-desktop-minimal, most are still on 20.04, new stations are all deployed with 22.04 (with a ubuntu-desktop-minimal --no-install-recommends flag for 22.04). Users need to be able to interact with network settings GUI, so we use NetworkManager, set via netplan, to manage network settings.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]We are running into an interesting issue with Ubuntu Server 22.04 where after running a netplan to set static IP/DHCP settings on the 2 NIC ports on the client, they will, after some number of reboots, "flip" where the MAC that was on eth0 will show up as the MAC address for eth1. Physically swapping the cable to eth1 will restore connection with the static IP assigned originally to eth0. After another reboot, the ports will flip back (requiring another cable change if that was swapped in the process as well). In our experience, the swap has not happened again.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]This is a significant issue for us, as anytime one of these systems is added/replaced, it is basically a ticking clock waiting for it to come back from a reboot with an unresponsive network.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Has anyone seen of, or even heard of, an error like this? I have a bunch more information, wanted to keep the top post reasonable, happy to provide additional details (limted by post length)[/FONT][/COLOR]

---

### Post by TheFu on 2024-02-28
The order that the kernel discovers the NICs can change due to kernel timing.  

Pre-20.04, systemd was assigning unique NIC device names using the MAC address for part of the name.  For many users, those with single NIC setups, this was a pain. We just wanted eth0 and eth1.  

The compromise seems to have been related to the driver used for the first part of the name **ens**, **enp**, you get the idea.  Here's the documentation:
[https://www.freedesktop.org/software/systemd/man/latest/systemd.net-naming-scheme.html](https://www.freedesktop.org/software/systemd/man/latest/systemd.net-naming-scheme.html)

Once you get the unique names, then just modify netplan on each system for those names.  Something like Ansible should handle that easily.
You could look in /sys/class/net/ (at least in the 5.xx kernels) to get the device names.  udev can be used to set them too, using the documented variables, I think.

Anyway, hope this is helpful.

---

