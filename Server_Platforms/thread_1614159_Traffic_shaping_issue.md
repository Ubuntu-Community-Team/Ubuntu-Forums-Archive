---
title: "Traffic shaping issue"
date: 2010-11-05
forum: Server Platforms
---

### Post by BajaMnstr on 2010-11-05
Hello everyone,

I currently am running Ubuntu-server x64 8.04LTS on a Dell 860 Server. On that I have running iptables for firewall access control, then tc for traffic control running HTB qdiscs, The traffic shaper is running transparently and is shaping based on the mac address of each packet. 

For quite a while this system has worked perfectly, but now that I'm close to shaping for 1000+ users over a DS3 line, It's having issues shaping the traffic correctly. The upload generally is the hardest hit, sometimes it is dead on, other times it's half of the CIR. 

I've come close to a solution but haven't found one. I tried removing the Segmentation offload from the NIC using ethtool -K thinking that might help. But no dice.

I'm kinda thinking along the lines that maybe the system timer needs to be adjusted in the kernel. "CONFIG_HZ=" Currently in the config in /boot it's set to 100. Does anyone have experience modifying this? or does anyone possibly have any suggestions?

Thanks in Avance

-Wayne

---

