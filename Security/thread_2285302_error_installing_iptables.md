---
title: "error installing iptables"
date: 2015-07-04
forum: Security
---

### Post by sajil2 on 2015-07-04
hi there i am using  ubuntu 12.04 i get error while installing iptables.



Do you want to continue [Y/n]? Y
Setting up iptables-persistent (0.5.3ubuntu2) ...
FATAL: Could not load /lib/modules/2.6.32-042stab108.5/modules.dep: No such file or directory
dpkg: error processing iptables-persistent (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 iptables-persistent
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by cariboo on 2015-07-04
Unless you uninstalled iptables, you shouldn't need to, as it is installed by default. If you want to check if it is installed use the following command:

```
which iptables
```

which should give you the following output:

```
which iptables
/sbin/iptables
```

---

### Post by sajil2 on 2015-07-04
i ran the command which iptables. and i got this 
/sbin/iptables

what next i can do?

---

### Post by sajil2 on 2015-07-04
i did fresh instalation and started all over again i still get this.

sudo apt-get install iptables-persistent
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package iptables-persistent

---

### Post by cariboo on 2015-07-05
Why do you want to install iptables-persistent? You have iptables installed, all you need is to create a set of rules, using gufw.
To start the firewwall from the command line use the following command:

```
sudo ufw enable
```

once you started it, use:

```
sudo ufw status
```

to check the rules use:

```
sudo ufw status verbose
```

the output of a default install should look something like this:

```
cariboo@alexis:~$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip
```

Once you've made sure the firewall is up and running you can check the default rules using;

```
sudo iptables -L
```

---

### Post by Doug S on 2015-07-06
It looks as though you are using an odd kernel, and so it is not surprising that iptables-persistent has trouble installing.
What do you get for "uname -a"? On my 12.04 ubuntu server I get:```
doug@doug-64:~/tcpdump/077$ uname -a
Linux doug-64 3.2.0-86-generic #123-Ubuntu SMP Sun Jun 14 18:13:12 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```
iptables-persistent solves a problem that does not exist anyhow, as there are other ways to make your rule set load during boot. For example, here is what I do:```
doug@doug-64:~/tcpdump/077$ [COLOR=#ff0000]cat /etc/network/interfaces[/COLOR]
# Smythies 2011.11.15 Can I execute my firewall script from here
#          instead of /etc/rc2.d? Add it.
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
[COLOR=#ff0000]pre-up /home/doug/init/doug_firewall[/COLOR]

# The primary interface (d-link PCI card)
auto eth1
iface eth1 inet dhcp

# Local network interface (uses built in ethernet port)
auto eth0
iface eth0 inet static
  address 192.168.111.1
  network 192.168.111.0
  netmask 255.255.255.0
  broadcast 192.168.111.255
```

---

