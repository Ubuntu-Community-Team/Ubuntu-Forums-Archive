---
title: "Sonicwall and Virtualization How To"
date: 2008-08-16
forum: Virtualisation
---

### Post by Blind Tiger on 2008-08-16
In the event that others experience the same dilemma that I did, I would like to post this brief how to as a head ache saving resource!

Conditions are:
[LIST=1]
[*]Ubuntu is your host OS
[*]XP Pro is your guest OS
[*]You are using Sonicwall Global VPN Client on XP
[*]Your network adapter is set to NAT within your virtualization application
[/LIST]

To completely enable your sonicwall network adapter on the XP guest, you will need to Enable NAT Traversal on the Advanced section of the VPN menu on Sonicwall's web administration page.  This will allow your GVC to establish a vpn and secure a stable ip address.  Our office uses the Sonicwall TZ170, and this setting, saved to the sonicwall configuration, works.

I have confirmed that this works for Ubuntu 8.04.1 host running XP Pro SP3 as a guest within both VMware 1.0.6 and VirtualBox 1.6.4 using Sonicwall Global VPN Client 4.0.0.835.

---

