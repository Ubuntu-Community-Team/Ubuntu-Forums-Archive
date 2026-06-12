---
title: "ufw forwarding 18.04"
date: 2020-01-29
forum: Server Platforms
---

### Post by beduntu on 2020-01-29
Hi everyone, I have read various threads and docs on the subject but now I am stuck and need help.

Situation: small cluster, master node with 4 nics, salve nodes with 1 nic, ip addresses are all static, master and slaves are connected through a switch

Master ip
  eno1: 10.10.0.100
  james: 192.168.1.100, james it's a 3 nics bond (eno2, eno3, eno4)  

Slave node1 ip
 eno1: 192.168.1.101, for node2, 3,..., change the last octet only as 102, 103 and so on.

Masters and nodes communicate with each other, master can reach the Web, nodes now cannot: how can I do for update/upgrade the nodes? 

Forwarding between james and eno1 on master is required, and in the slave nodes netplan config I put as gateway4 the james's ip:

Master Netplan:

```
network:
    version: 2
    ethernets:
        eno1:
            addresses:
            - 10.10.0.100/23
            gateway4: 10.10.1.254
            nameservers:
                addresses:
                - 10.10.10.5
                - 10.10.20.6
        eno2:
          dhcp4: false
          dhcp6: false
        eno3:
          dhcp4: false
          dhcp6: false
        eno4:
          dhcp4: false
          dhcp6: false
    bonds:
      james:
        addresses: [192.168.1.100/24]
        interfaces:
          - eno2
          - eno3
          - eno4
        parameters:
          mode: 802.3ad
          mii-monitor-interval: 1
```

node1 netplan:

```

network:
    ethernets:
        eno1:
            addresses:
              - 192.168.1.101/24
            gateway4: 192.168.1.100
            nameservers:
                addresses:
                - 8.8.8.8
        eno2:
            dhcp4: no
            optional: true
        eno3:
            dhcp4: no
            optional: true
        eno4:
            dhcp4: no
            optional: true
    version: 2

```

As suggest for example [here ]("https://www.cyberciti.biz/faq/how-to-configure-ufw-to-forward-port-80443-to-internal-server-hosted-on-lan/")and [here ]("https://ubuntuforums.org/showthread.php?t=833844")I have:
- modify the file  ***/etc/default/ufw*** and set ***DEFAULT_FORWARD_POLICY="ACCEPT"***
- modify the file ***/etc/sysctl.conf*** and set ***net.ipv4.ip_forward=1***
- insert this rule: ***ufw route allow in on eth1 out on james***

and restarted the services, now my ufw status:

```
To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere
443/tcp                    ALLOW       Anywhere
389/tcp                    ALLOW       Anywhere
636/tcp                    ALLOW       Anywhere
88/tcp                     ALLOW       Anywhere
464/tcp                    ALLOW       Anywhere
22/tcp (v6)                ALLOW       Anywhere (v6)
80/tcp (v6)                ALLOW       Anywhere (v6)
443/tcp (v6)               ALLOW       Anywhere (v6)
389/tcp (v6)               ALLOW       Anywhere (v6)
636/tcp (v6)               ALLOW       Anywhere (v6)
88/tcp (v6)                ALLOW       Anywhere (v6)
464/tcp (v6)               ALLOW       Anywhere (v6)

Anywhere on james          ALLOW FWD   Anywhere on eno1
Anywhere (v6) on james     ALLOW FWD   Anywhere (v6) on eno1

```

from salve nodes I can ping the master eno1 nic but they don't reach his gateway nor internet so I can't perform the update/upgrade/install actions.

What is missing? Doubt: must i also enable the IP masquerading?
Tnk's

B-)

---

### Post by TheFu on 2020-01-30
I don't think ufw supports packet routing. For that, you need iptables.

---

