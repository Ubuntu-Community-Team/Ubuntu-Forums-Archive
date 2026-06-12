---
title: "[SOLVED] Guest OS Networking on new VMware ESXi 3.5 install"
date: 2008-09-09
forum: Virtualisation
---

### Post by Kolipoki on 2008-09-09
Hi,

I'm new to Ubuntu (using server edition) and to VMware. Installed ESXi 2 days ago, then installed Hardy as guest OS, but having some trouble with networking. 

I can Putty Ubuntu from LAN and can use the Infrastructure client from ESX to use CLI, but can't apt-get repos or reach outside. Network configurations have been set exactly as (static IP) I have done successfully before in previous Ubuntu 8.04 installations as host OS. 

Not sure if guest OS (Hardy in this case) needs IPs and gateway set in a different manner than when it's configured as host. I'm probly missing something simple, but it's my first time doing this combo :)

Searched forums enough but didn't find this (ESXi) subject. Any lead will be greeeatly appreciated. Thanks in advance.

EDIT: Fixed, was an issue with firewall.

---

