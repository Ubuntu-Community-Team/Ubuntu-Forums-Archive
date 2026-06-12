---
title: "Problem - Ubuntu 16.04.3 Guest Weekly Freezes under KVM / oVirt"
date: 2018-02-15
forum: Virtualisation
---

### Post by linuksguru on 2018-02-15
[COLOR=#000000][FONT=Helvetica]Hi ![/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]I have strange and annoying problem with one VM on oVirt node 4.2 - weekly freezes of Ubuntu 16.04.3 with ISPConfig 3.1 active.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]ISPConfig is a Web GUI frontend (written in PHP) to Apache, Postfix, Dovecot, Amavis, Clam and ProFTPd.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Separate engine PC, not hosted engine.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Ubuntu 16.04.3 LTS (Xenial Xerus), 2 cores allocated, 8 GB RAM (only fraction is being used).[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]kernel 4.13.0-32-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]6300ESB Watchdog Timer[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Memory ballooning disables, and there are always about 7 GB of free RAM left.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]4 VMs active, CPU load on node is low.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Tried several kernel versions, no change.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]I can&#8217;t trace any problem in the log on Ubuntu guest. Even watchdog timer 6300ESB configured to reset does nothing (what is really strange).[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]VM stops responding even to pings, VM screen is also frozen.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]oVirt engine don&#8217;t display IP address anymore, it means ovirt-guest-agent is dead.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]VM is in DMZ, and not connected to ovirtmgmt, but rather to bridged Ethernet interface.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]in oVirt I have defined network "DMZ Node10-NIC2&#8221;.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
On CentOS 7 host node (NOT Ubuntu KVM Guest):[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]cd /etc/sysconfig/network-scripts/[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]tail ifcfg-enp3s4f1[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]DEVICE=enp3s4f1[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]BRIDGE=ond04ad91e59c14[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]ONBOOT=yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]MTU=1500[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]DEFROUTE=no[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]NM_CONTROLLED=no[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]IPV6INIT=no[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Googling doesn&#8217;t show anything useful except attempt to change kernel version what I already did.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
Any idea how to fix this freeze ?[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Thanks in advance for any help.[/FONT][/COLOR]

---

### Post by TheFu on 2018-02-15
If KVM is being used, then RAM issues can cause a VM to stop working.
If KVM is being used, storage read failures can cause a VM to stop working, but normally it is "paused", not crashed.

I would take the VM and run it on an Ubuntu host running KVM directly.  See if the problem continues.  None of my KVM VMs running Ubuntu under Ubuntu show any issues.  I do have a Windows VM that fails (pauses) about 2-times a month without warning.  I think it was bit-rot, so I moved the VM to new storage and had Windows tools fix the corruption inside the VM.  It has only been a few days, so I cannot say whether my efforts helped or not.  

What do the system log files show on the host system? Anything there?  Anything in the oVirt host logs?

You asked for ideas.

I've never used oVirt.  We aren't big enough to need that overheard.

---

### Post by linuksguru on 2018-02-16
Thanks for reply! Unfortunately, it is critical infrastructure software and can't be moved anywhere out from oVirt environment. I'll add another node in a short time and look what happens.
So far I simply restart server on scheduled interval.

---

### Post by TheFu on 2018-02-16
> **linuksguru said:**
> Thanks for reply! Unfortunately, it is critical infrastructure software and can't be moved anywhere out from oVirt environment. I'll add another node in a short time and look what happens.
So far I simply restart server on scheduled interval.

You put critical infrastructure on CentOS?  Can you switch it over to paid RH support and get help from them?
**$ journalctl -k -b -p err** show anything?

---

### Post by foro.carlos on 2018-03-27
> **linuksguru said:**
> [COLOR=#000000][FONT=Helvetica]Hi ![/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]I have strange and annoying problem with one VM on oVirt node 4.2 - weekly freezes of Ubuntu 16.04.3 with ISPConfig 3.1 active.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]ISPConfig is a Web GUI frontend (written in PHP) to Apache, Postfix, Dovecot, Amavis, Clam and ProFTPd.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Separate engine PC, not hosted engine.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Ubuntu 16.04.3 LTS (Xenial Xerus), 2 cores allocated, 8 GB RAM (only fraction is being used).[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]kernel 4.13.0-32-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]6300ESB Watchdog Timer[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Memory ballooning disables, and there are always about 7 GB of free RAM left.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]4 VMs active, CPU load on node is low.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Tried several kernel versions, no change.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]I can’t trace any problem in the log on Ubuntu guest. Even watchdog timer 6300ESB configured to reset does nothing (what is really strange).[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]VM stops responding even to pings, VM screen is also frozen.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]oVirt engine don’t display IP address anymore, it means ovirt-guest-agent is dead.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]VM is in DMZ, and not connected to ovirtmgmt, but rather to bridged Ethernet interface.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]in oVirt I have defined network "DMZ Node10-NIC2”.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
On CentOS 7 host node (NOT Ubuntu KVM Guest):[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]cd /etc/sysconfig/network-scripts/[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]tail ifcfg-enp3s4f1[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]DEVICE=enp3s4f1[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]BRIDGE=ond04ad91e59c14[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]ONBOOT=yes[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]MTU=1500[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]DEFROUTE=no[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]NM_CONTROLLED=no[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]IPV6INIT=no[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Googling doesn’t show anything useful except attempt to change kernel version what I already did.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
Any idea how to fix this freeze ?[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Thanks in advance for any help.[/FONT][/COLOR]

Hi, we are experiencing the same problem with proxmox/KVM/QEMU with some ubuntu 16.04 machines as well. Same kind of random Total pause of the machine 

Would you mind to share the hardware details of your machine?

Have you tried to launch the KVM in the foreground to see if it spits some errors ?  We get this ([kernel.org case that matches ours]("https://bugzilla.kernel.org/show_bug.cgi?id=197813") ) 
```
KVM: entry failed, hardware error 0x5
```

---

### Post by linuksguru on 2018-03-27
Hi !

I'm running oVirt 4.2 (KVM front-end) on HP ProLiant G6, Dual Xeon CPU, 28 GB RAM. VM disk images stored on separate hardware RAID L1 2TB (SmartArray P410i, WD NASware hard drives 2TB / 7200 rpm).
Firmware and BIOS are latest versions available. CPU load is low, memory consumed to about 75%.

Unfortunately, problem still exists. I upgraded kernels on both host and guest, turned off some services and weekly tasks like fstrim.
Ubuntu 16.04 LTS guest still freezes on weekends about once per 2 weeks.

I examined logs on host and guest, found nothing that could help.

---

### Post by TheFu on 2018-03-27
So ... I switch a VM over to using virt-SCSI/SATA devices.  That VM has been stable.  However, my desktop VM did lock up on Saturday morning which is still straight virtio drivers.  The other 15 VMs on that same physical system didn't have any issues.

Proliant G6 ... ?
* [http://h17007.www1.hpe.com/us/en/enterprise/servers/supportmatrix/ubuntu.aspx](http://h17007.www1.hpe.com/us/en/enterprise/servers/supportmatrix/ubuntu.aspx)
* [https://certification.ubuntu.com/server/models/?query=&vendors=HPE&release=16.04+LTS](https://certification.ubuntu.com/server/models/?query=&vendors=HPE&release=16.04+LTS) 
 It really shouldn't matter inside a VM, but you never know.

---

### Post by linuksguru on 2018-03-27
All my disks connected via virt-SCSI.

Other VMs, including Windows, run just fine.
Possibly unfortunate combination of hardware and software.

VMs from this test ProLiant are being moved to another Xeon server, yet I don't know what to do with this particular VM.

---

### Post by linuksguru on 2018-03-27
> **foro.carlos said:**
> Hi, we are experiencing the same problem with proxmox/KVM/QEMU with some ubuntu 16.04 machines as well. Same kind of random Total pause of the machine 

Would you mind to share the hardware details of your machine?

Have you tried to launch the KVM in the foreground to see if it spits some errors ?  We get this ([kernel.org case that matches ours]("https://bugzilla.kernel.org/show_bug.cgi?id=197813") ) 
```
KVM: entry failed, hardware error 0x5
```

What are your hardware details ?
In my case KVM is controlled by oVirt, I have few option to control it.

---

### Post by foro.carlos on 2018-04-05
> **linuksguru said:**
> Hi !

I'm running oVirt 4.2 (KVM front-end) on HP ProLiant G6, Dual Xeon CPU, 28 GB RAM. VM disk images stored on separate hardware RAID L1 2TB (SmartArray P410i, WD NASware hard drives 2TB / 7200 rpm).
Firmware and BIOS are latest versions available. CPU load is low, memory consumed to about 75%.

Unfortunately, problem still exists. I upgraded kernels on both host and guest, turned off some services and weekly tasks like fstrim.
Ubuntu 16.04 LTS guest still freezes on weekends about once per 2 weeks.

I examined logs on host and guest, found nothing that could help.

hi, Can you launch this to see the exact model of CPU?


```
cat /proc/cpuinfo | grep "model name"
``` 

ours is "model name	: Intel(R) Xeon(R) CPU E5-2650 v4 @ 2.20GHz
"

---

### Post by linuksguru on 2018-04-05
model name    : Intel(R) Xeon(R) CPU           E5620  @ 2.40GHz

---

### Post by TheFu on 2018-04-06
Seems this issue isn't specific to Ubuntu. A friend, who  works in a RHEL/CentOS shop with PB of data says this:
> Ovirt on centos - connection issues between manager and all VMs, not os specific. Most of my VMs are also centos. 10Gbps network, gluster storage for replication x3, semi-periodic connection issues still in troubleshooting mode.

---

### Post by foro.carlos on 2018-04-19
Is pretty strange then... i'm testing ESXi (cause Dell Support asked me to do so) and trying to force a crash or freeze or something in case is hardware related but I think is not going to happen again. So it could be something in the kernel that only happen in very specific cases. 

In any case we are running out of options here. we tried lots of things , BIOS upgrades and downgrades, several kernels, several storages, lots of memory tweaks, No matter what we try some machines (ubuntu mostly) freeze without any trace or clue about why...

We are thinking in trying XEN and see if it makes a diference

---

### Post by TheFu on 2018-04-19
Appears from here to be something related to oVirt/KVM on CentOS.

---

### Post by foro.carlos on 2018-04-20
In our case is KVM but in Ubuntu 16.04 and Proxmox as the manager... so, Kernel and KVM in common. Not even the CPU gen since we have a modern model and almost identical models without any problems.

---

