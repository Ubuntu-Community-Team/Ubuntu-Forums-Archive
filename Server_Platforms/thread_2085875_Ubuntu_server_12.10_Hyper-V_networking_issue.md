---
title: "Ubuntu server 12.10 Hyper-V networking issue"
date: 2012-11-19
forum: Server Platforms
---

### Post by jon27 on 2012-11-19
Hi all,

I am by no means a linux "expert" so please be gentle with me.

I am having issues with networking in hyper-v after moving the vhd to another host and recreating the Virtual Machine. In fact, this has happened on 2 separate instances. It worked on the original host and i have others running successfully. 

All appears to be ok except i cannot ping another ip or remotely ping / connect to it.

eth0 is configured as a static address. 

lshw -C network produces
```
*-network
description : ethernet interface
physical id : 1
logical name : eth0
serial L 00:15:5d:00:0d:06
capabilities : ethernet physical
configuration : broadcast=yes driver=hv_netsvc driverversion=3.1 firmware=N/A ip=192.168.0.61 link=yes multicast=yes

```

lsmod produces
```

...
hv_netsvc 22702 0
...
hv_vmbus 34460 4
...

```

I dont see anything in any logs that would indicate any problems.

I am really stuck and would appreciate any help or pointers anyone can offer me. I don't want to have to reinstall the o/s each time i need to move a virtual machine.

Thanks 

JJ:confused:

---

### Post by jon27 on 2012-11-19
It would appear that the issue is actually the host machine as i've just tried doing the same to another host and it seems to work fine.

Appologies in advance.

---

### Post by Jayton on 2013-02-21
Are you sure it was just that? 

I've recently had problems with upgrading Ubuntu from 11.10 to 12.04, in a Hyper-V guest for a 3rd party system of a customer. The Ubuntu server would respond to pings for about 10 seconds on boot up, then stop responding. 

After checking /var/log/kern.log and a bit of Googling it appears this is caused by the IRQBALACNCE service on some versions of Ubuntu & Fedora when being upgraded on a Hyper-V guest, possibly other variants too.

Disable it by changing Enabled="1" to a 0 in /etc/default/irqbalance and reboot. This resolved our issue with networking problems after the upgrade.

---

