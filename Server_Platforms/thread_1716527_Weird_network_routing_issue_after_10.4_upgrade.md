---
title: "Weird network routing issue after 10.4 upgrade"
date: 2011-03-28
forum: Server Platforms
---

### Post by Corvias on 2011-03-28
I have a server which was previously running Ubuntu 8.04 64bit. A couple days ago, I upgraded it to 10.4. All seemed to be fine, until I realized that there were some strange network issues occurring

This server has two NIC's in it and each one is connected to a different subnet. each of those subnets access the same router, but through different addresses.

When both eth0 (connected on Subnet A) and eth1 (on Subnet B) are up, clients on A cannot reach eth1 and folks on B cannot reach eth0. If I bring one of the NIC's down, both subnets can access the other NIC fine.

As far as I can tell, no configurations have changed from before the upgrade, and everything was working as it should before the upgrade.

You might be wondering why I have such a bizarre setup -- its complicated, but suffice to say it has to do with Samba. I can explain it if you really want.

My /etc/network/interfaces looks like this:

```
iface eth0 inet static
        address xxx.yyy.1.6
        netmask 255.255.254.0
        gateway xxx.yyy.1.1

iface eth1 inet static
        address aaa.bbb.2.6
        netmask 255.255.252.0


```
(Yes, I know there is no gateway set for the second NIC.This is the configuration that has worked fine for the last two years. I've tried adding in the other gateway, but to no avail.)

Here is the output of route:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xxx.yyy.1.0     *               255.255.254.0   U     0      0        0 eth0
aaa.bbb.2.0     *               255.255.252.0   U     0      0        0 eth1
default         name-of eth0-gw 0.0.0.0         UG    100    0        0 eth0

```

Please, please help! Let me know if there is any other info you need.

---

### Post by Corvias on 2011-03-30
This has sunk to page four, so I don't feel so bad about bumping. Please help! I'll be happy with some commands or logs to watch to figure this out on my own!

---

### Post by Corvias on 2011-03-30
I figured out the solution to this problem on my own. For those who come here in the future with a similar issue, I found [this site]("http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/"), which describes (with a couple modifications) how to do what I needed done. Sorry none of you forum folks were able to help.

---

