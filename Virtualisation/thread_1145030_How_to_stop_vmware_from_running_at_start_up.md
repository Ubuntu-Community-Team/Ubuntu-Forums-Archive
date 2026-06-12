---
title: "How to stop vmware from running at start up?"
date: 2009-05-01
forum: Virtualisation
---

### Post by xoros on 2009-05-01
Like title says, I notice there is a bunch of vmware's processes that load when I boot up ubuntu

Is there any way to stop this? 

I want to only have the processes running when I load up vmware.

---

### Post by Legace on 2009-05-01
System -> Preferences -> Startup Applications

---

### Post by xoros on 2009-05-01
> **Legace said:**
> System -> Preferences -> Startup Applications

There is no options for vmware there. 
see pic

[[IMG]http://img172.imageshack.us/img172/7393/startupvmware.th.png[/IMG]](http://img172.imageshack.us/my.php?image=startupvmware.png)

This is what gets loaded at start up:
```
root      3611  0.0  0.0   4304   528 ?        Ss   08:15   0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid -n
root      3626  0.0  0.0   4280   312 ?        Ss   08:15   0:00 /usr/bin/vmnet-netifup -d /var/run/vmnet-netifup-vmnet1
root      3637  0.0  0.0  11092   488 ?        Ss   08:15   0:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet1/dhcpd/dhcpd
root      3655  0.0  0.0   4280   308 ?        Ss   08:15   0:00 /usr/bin/vmnet-netifup -d /var/run/vmnet-netifup-vmnet8
root      3669  0.0  0.0  11092   492 ?        Ss   08:15   0:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet8/dhcpd/dhcpd
root      3674  0.0  0.0   8996   668 ?        Ss   08:15   0:00 /usr/bin/vmnet-natd -d /var/run/vmnet-natd-8.pid -m /va
root      3950  0.0  4.8 620012 194000 ?       Ssl  08:15   0:09 /usr/lib/vmware/webAccess/java/jre1.5.0_15/bin/webAcces
root      3951  0.0  0.0  17568   792 ?        Ss   08:15   0:00 /usr/sbin/vmware-authdlauncher
root      4085  0.0  0.0   6488  1068 ?        S    08:15   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-c
root      4089  0.0  1.2 127212 49636 ?        Ssl  08:15   0:03 /usr/lib/vmware/bin/vmware-hostd -a -d -u /etc/vmware/h

```

How do I control that ??

---

### Post by dsavi on 2009-05-02
I think you should know that most of the VMware services *must* start on startup. On Windows anyway, if I didn't let vmware-(natd|authd|dhcpd|etc.) start up, VMware would not work even if I started the services manually. The actual Vmware program, however can be disabled without effect.

---

### Post by xoros on 2009-05-02
> **dsavi said:**
> I think you should know that most of the VMware services *must* start on startup. On Windows anyway, if I didn't let vmware-(natd|authd|dhcpd|etc.) start up, VMware would not work even if I started the services manually. The actual Vmware program, however can be disabled without effect.

I thought maybe in a unix/linux environment you could start/stop the services manually.

---

### Post by hal9ksrc on 2010-11-08
from command line: sudo ps-ax | less

you will prompted for the root password, then you will be watching a scrollable window in which you can use your arrow keys to move up and down to look for vmware PID'S . . . write down the pid's for each vmware process.  Tap the 'q' key to quit scoll window.

back at command line: sudo kill pid, pid pid

you can kill any pid from the command line in root

---

