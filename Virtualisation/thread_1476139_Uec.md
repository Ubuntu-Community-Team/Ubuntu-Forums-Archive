---
title: "Uec"
date: 2010-05-07
forum: Virtualisation
---

### Post by bmullan on 2010-05-07
I just installed a default UEC on 2 machines.

machine A has the cloud controller (CLC), walrus etc installed on it

machine B has the Node Controller installed.

both are plugged into a 100Mbps switch.

Also plugged into the switch is a 802.11N bridge

that bridge connects that LAN segment to my wireless network (192.168.1.x)

From other machines on the wireless network I can use a browser to 
get to my CLC.

**Two problems:**

I was only able to launch an instance successfully as root
not as another "user".

After the instance is launched I could not ssh to the instance IP (192.168.1.200).

One thing I noticed is that the IP address and mask for the VM created was

192.168.1.200 255.255.255.255

which I thought was odd since the rest of the network is a Class C

192.168.1.107 255.255.255.0 ---- for instance is my own PC.

So why is the mask automatically set to 255.255.255.255 or is that a bug ?

Because of that netmask difference I'm not even able to ping the VM from machines other than the Node Controller and the CLC.

---

