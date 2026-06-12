---
title: "NIC Alias not working"
date: 2012-01-25
forum: Server Platforms
---

### Post by zietbukuel on 2012-01-25
Hello, I'm trying to setup an alias for my bridge interface, but it won't start up using the /etc/network/interfaces file, but it does work if I use ifconfig directly, the problem is that I want this to be permanent.

This is what I get when I use the interfaces file and then restart the network interfaces:

```
$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                      ssh stop/waiting
ssh start/running, process 1957

Waiting for br0 to get ready (MAXWAIT is 20 seconds).
ssh stop/waiting
ssh start/running, process 2097
RTNETLINK answers: File exists
Failed to bring up br0:0.
```

I need it to be an alias of br0 not eth0, I need the bridge for KVM. I'm using Ubuntu Server 11.10

---

### Post by SeijiSensei on 2012-01-25
> it does work if I use ifconfig directly, the problem is that I want this to be permanent.

If you want it to come up at boot, just stick the appropriate ifconfig statement in /etc/rc.local.  That file contains any commands that should be run as the boot process comes to an end.

---

### Post by zietbukuel on 2012-01-25
It was working previously, but it stopped working and now I get this message when I try to execute the command:

```
ifconfig br0:0 100.101.102.210 netmask 255.255.255.0
```

```
SIOCSIFFLAGS: Cannot assign requested address
```

---

### Post by SeijiSensei on 2012-01-25
I take it "ifconfig br0" shows the adapter with its already assigned IP address?  

Is the virtual interface in the same network subnet as the physical interface?  We had a question about this just the other week, and I don't think we ever heard back whether it's possible or not.  When I've used virtual adapters, it's been to set another address in the same subnet, e.g,

```
ifconfig eth0   10.1.1.1 netmask 255.255.255.0 broadcast 10.1.1.255
ifconfig eth0:0 10.1.1.2 netmask 255.255.255.0 broadcast 10.1.1.255
```

---

### Post by zietbukuel on 2012-01-26
Yes, br0 has a public static IP and I want it to have a local IP as well.

---

### Post by zietbukuel on 2012-01-26
Nevermind, I did this in the virtual machine and it worked, thanks for any help.:D

---

