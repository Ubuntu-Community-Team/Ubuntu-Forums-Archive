---
title: "Multiple network interfaces on Mac OSX"
date: 2024-07-10
forum: Virtualisation
---

### Post by devlaps on 2024-07-10
Hi Folks, I'd like to create instances that have multiple interfaces. One interface, connects to a shared interface out to the Internet, the other instance connected to a private bridge on my MBP.

I found some posts online and it looks like folks have done it before, but it's not working for me. Here's have I've done:

[COLOR=#839496][FONT=Menlo][FONT=courier new]sudo ifconfig bridge200 create
sudo ifconfig bridge200 inet 192.168.10.1 netmask 255.255.255.0
sudo ifconfig bridge200 up[/FONT]
[/FONT][/COLOR]
Followed by:

[FONT=courier new][COLOR=#839496]multipass launch -n first-vm --cpus 4 --disk 20G --memory 8G --cloud-init cloud-init.yaml [COLOR=#CB4B16]\[/COLOR]
        --network en0  [COLOR=#CB4B16]\[/COLOR]
        --network name=bridge200,mode=manual
[/COLOR][/FONT]
When I do this, I get the following error:

[FONT=courier new]launch failed: Invalid arguments supplied
Invalid network options supplied[/FONT]

I can see the bridge on my laptop:

[FONT=courier new]bridge200: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        options=63<RXCSUM,TXCSUM,TSO4,TSO6>
        ether XX:XX:XX:XX:XX:XX
        inet 192.168.10.1 netmask 0xffffff00 broadcast 192.168.10.255
        Configuration:
                id 0:0:0:0:0:0 priority 0 hellotime 0 fwddelay 0
                maxage 0 holdcnt 0 proto stp maxaddr 100 timeout 1200
                root id 0:0:0:0:0:0 priority 0 ifcost 0 port 0
                ipfilter disabled flags 0x0
        media: <unknown type>
        status: inactive[/FONT]

However, Multipass networks does not see the bridge:

[FONT=courier new]&#10095; mp networks
Name   Type       Description
en0    wifi       Wi-Fi
en4    ethernet   Ethernet Adapter (en4)
en5    ethernet   Ethernet Adapter (en5)
en6    ethernet   Ethernet Adapter (en6)
en7    usb        USB 10/100/1000 LAN[/FONT]

Greatly appreciate any pointers!

Dave.

---

### Post by devlaps on 2024-07-12
It seems like this is not a common problem folks have. I've started reading through the Multipass source code and feel pretty good about being able to fix this. Please PM me or ping me here if you are interested in what I find.

Dave.

---

