---
title: "I guess my Ubuntu server is being hacked, eveytime I log in, this will appear"
date: 2022-11-19
forum: Security
---

### Post by lazzalee on 2022-11-19
Hello guys. I need some help from you guys. I set up a VPN on Tencent Cloud(a cloud server provider from China), and the server is Ubuntu 20.04 LTS. The problem is this, everytime I log into my ubuntu account (non-root user), these annoying codes will appear within 3 minutes. Please see picture attached.

Any idea what happened to my server? What should I do to solve the problem?

Thanks!

---

### Post by TheFu on 2022-11-19
On a poorly secured LAN, seeing firewall messages is common.  "Internet background noise" is the term I've heard.  100% expected.
BTW, if you don't physically control the disk, storage, NIC, and DNS there is little that can be done to fully secure a system.  Last time I checked, the CCP was blocking all TLS v1.3 traffic which I use to drastically cut attempted attacks to my server systems outside their control.

You can tell ufw to be quiet about DROPped packets.  I don't know how off the top of my head.

Lastly, please don't post images of text.  'dmesg' has those.  I bet the boot log does too - 'journalctl -b', so you can use ssh to select/paste the information from anywhere in the world.  Always use key-based ssh connections into that system, if you can.

---

### Post by QIII on 2022-11-19
The UF does not support circumvention of regional laws and regulations enforced by legal jurisdictions.  

We are not lawyers.  We do not claim to be experts in the laws of all jurisdictions.  We do, however, understand that some jurisdictions are very harsh in their enforcement and that grave consequences can accompany infractions.

As this does appear to be related to Government policy, this thread is closed.

---

