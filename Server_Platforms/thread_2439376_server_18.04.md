---
title: "server 18.04"
date: 2020-03-26
forum: Server Platforms
---

### Post by mikelhayes on 2020-03-26
I must say setting a static via file is not fun.
Current server has 4 eth.
network:
    ethernets:
        eno1:
            dhcp4: true
        eno2:
            dhcp4: true
        eno3:
            dhcp4: true
        eno4:
            dhcp4: true
    version: 2



I'd like to set en04 to a static BUT 50-cloud-init.yaml will not accept it seems any type on indent w/o complaining. My last attempt was
network:
    ethernets:
        eno1:
            dhcp4: true
        eno2:
            dhcp4: true
        eno3:
            dhcp4: true
    version: 2
    renderer: networkd
        eno4:
            dhcp: no
            addresses: [10.0.30.10/23]
            gateway4: 10.0.30.1
            nameservers:
              addresses: [10.0.0.21,10.0.2.21]
1-3 can stay dhcp or inactive. Just trying to make a static on 4.

---

### Post by darkod on 2020-03-27
When posting that type of output please post it inside CODE tags. Otherwise it loses the format.

As you can see by looking at your own post all indent was lost and no one can confirm if what you have is valid by looking at the post.

Post the output again inside CODE tags.

---

### Post by mikelhayes on 2020-03-27
thanks

---

### Post by LHammonds on 2020-03-29
I think this was the very first issue I had with the new 'default' image for the server install...which is part of the reason why I do not use the 'default' installer anymore.

I use the alternative installer...also known as traditional installer which also allows you to configure LVM/RAID which the default will not for whatever reason.

Here is [how I install Ubuntu Server]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244#p616") (linked directly to the network configuration section)

**EDIT:** Found the thread used to [note the differences between the LIVE and ALTERNATIVE installer]("https://ubuntuforums.org/showthread.php?t=2390785").

LHammonds

---

### Post by TheFu on 2020-03-29
Need to see correctly formatted YAML.

---

