---
title: "bond1: ERROR while getting interface flags: No such device"
date: 2010-10-14
forum: Server Platforms
---

### Post by ElllisD on 2010-10-14
On Ubuntu Server 10.10 the second bond device won't come up.
Someone please advise the correct configuration.


Error message when I run /etc/init.d/networking restart:

```
SIOCSIFADDR: No such device
bond1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
bond1: ERROR while getting interface flags: No such device
bond1: ERROR while getting interface flags: No such device
Failed to bring up bond1.
```


/etc/network/interfaces

```
auto bond0
iface bond0 inet static
    bond_miimon  100
    bond_mode balance-rr
    address  xxx.xxx.xxx.xxx
    netmask  255.255.255.0
    gateway  xxx.xxx.xxx.xxx
    up /sbin/ifenslave bond0 eth0 eth1
    down /sbin/ifenslave -d bond0 eth0 eth1
    dns-nameservers  xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
    dns-search  sub.domain.suffix

auto bond1
iface bond1 inet static
    bond_miimon  100
    bond_mode balance-rr
    address  xxx.xxx.xxx.xxx
    netmask  255.255.255.0
    gateway  xxx.xxx.xxx.xxx
    up /sbin/ifenslave bond1 eth2 eth3
    down /sbin/ifenslave -d bond1 eth2 eth3
    dns-nameservers  xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
    dns-search  sub.domain.suffix
```


/etc/modprobe.d/aliases.conf (inoperative method 1 of 2)

```
alias bond0 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200 maxbonds=2

alias bond1 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200 maxbonds=2
```


/etc/modprobe.d/aliases.conf (inoperative method 2 of 2)

```
alias bond0 bonding
alias bond1 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200 maxbonds=2
```

---

### Post by BobVila on 2010-10-14
Your 'maxbonds' is incorrect - needs an underscore. Try max_bonds=2

Also, that stuff should go in /etc/modprobe.conf, if I'm not mistaken. *I've only enabled bonds on CentOS/RHEL, so I'm not entirely sure on this bit*

---

### Post by ElllisD on 2010-10-14
> **BobVila said:**
> Your 'maxbonds' is incorrect - needs an underscore. Try max_bonds=2

Previous attempts indeed included the underscore there.

I'm trying each way I see online, a few blogs have different details on this.

I haven't tried any of the RHEL methods yet, soon will have no other option than to try that too.


/etc/modprobe.d/aliases.conf

```
alias bond0 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200 max_bonds=2

alias bond1 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200 max_bonds=2
```


/etc/modprobe.d/aliases.conf

```
alias bond0 bonding
alias bond1 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200 max_bonds=2
```

---

### Post by ElllisD on 2010-10-14
> **BobVila said:**
> should go in /etc/modprobe.conf

There's quite a few different methods online about how to do this, but they're old, some from 5 years ago- none are recent or functional anymore in 10.10 apparently.

Apparently Ubuntu's not doing it the RHEL way either, it didn't work when the lines were there.

/etc/modprobe.conf

```
alias bond0 bonding
alias bond1 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200 max_bonds=2
```


/etc/modprobe.d/aliases.conf

```
alias bond0 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200 max_bonds=2

alias bond1 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200
```

---

### Post by ElllisD on 2010-10-14
The device that's being reported as not present will obtain an ip address when configured alone.

When bonded it's not present.

This time I tried changing /etc/modprobe.d/aliases.conf to /etc/modprobe.d/aliases and it still didn't help.

---

### Post by ElllisD on 2010-10-14
[A partial solution]("http://ubuntuforums.org/printthread.php?t=1119460") is posted on another thread, but it doesn't persist through a reboot, plus when the second bond is up, the first one stops allowing transfers via sftp- and won't allow an additiona ssh session to connect.

Oh, well.

---

