---
title: "No Local Network Access, Services"
date: 2019-06-22
forum: Server Platforms
---

### Post by campbellsam97 on 2019-06-22
Hi,

I've just migrated my machine over to another one, and I've tried to bring the network connectivity back up since the device name changed to enp1s0 from enp2s0f0.

I assume I should do this by editing my /etc/network/interfaces file to use the name enp1s0 instead. However I was told in the file to use the YAML file under /etc/netplan instead, which I proceeded to do.
After a reboot the machine obtained an IP and is able to ping any computer on the network and external resources like google.ca. Alongside this, other machines are able to access services it is running like Plex and Resilio Sync.

However locally run services like SSH and Samba are no longer accessible.

What I have tried:
[LIST]
[*]I have tried reinstalling ifupdown, and adding the appropriate lines to /etc/network/inferfaces
[*]I have tried removing all YAML files in the netplan directory.
[*]I have tried iptables -F
[*]I have tried uninstalling cloud-init
[/LIST]

I've run out of ideas and would really prefer not to have to reinstall Ubuntu at this point. Does anyone have a suggestion?

---

### Post by TheFu on 2019-06-22
I had to add a setting to the sshd_config file to prefer IPv4 networking over IPv6 stuff on a few of my 16.04 systems.
I don't have any newer systems, mainly because of concerns about netplan with non-trivial network setups like mine.
sshd_config:  
```
AddressFamily inet
```
I can't help with samba, but I'd check that there isn't a specific interface listed in the config file for the listener.

---

### Post by houstonbofh on 2019-07-04
You are using netplan or network/interfaces.  Do not try and use both as netplan will just bulldog through.

If you are getting the correct IP, check your services cofig file and make sure they were not bound to a specific IP or interface.

---

