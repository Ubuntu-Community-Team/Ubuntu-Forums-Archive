---
title: "NIC inactive for Broadcom Corporation NetXtreme II BCM57711E 10-Gigabit"
date: 2015-09-27
forum: Server Platforms
---

### Post by ehsan9 on 2015-09-27
Hi 
Why showing NIC inactive for Broadcom Corporation NetXtreme II BCM57711E 10-Gigabit PCIe while installing Ubuntu on HP ProLiant BL460c G6. At the time of installation the two Ethernet Ports are detected but with ethtool show 'Link detected: no'. Link is down. that driver is bnx2x. how can i update driver or change it ? plz help me :-(

---

### Post by darkod on 2015-09-27
Have you checked /etc/network/interfaces to make sure the interfaces are set up to be activated on boot? Usually if it detects the interfaces during installation it should work fine. Do you have them configured, at least the primary one? And you have it connected to a switch or something? I assume the lights on the port are off?

---

### Post by lukeiamyourfather on 2015-09-29
By default interfaces are inactive. The only interface that would typically be active is the one used during the install (assuming one was used at all). 

[https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)

---

