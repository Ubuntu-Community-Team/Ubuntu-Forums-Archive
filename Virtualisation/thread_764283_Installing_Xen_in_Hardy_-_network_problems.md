---
title: "Installing Xen in Hardy - network problems"
date: 2008-04-23
forum: Virtualisation
---

### Post by akpuf on 2008-04-23
Hi.

So I'm trying to set up Xen on an amd64 Hardy server install.  I've been following the directions from [https://help.ubuntu.com/community/Xen]("https://help.ubuntu.com/community/Xen").  Basically, I've done the following:

1)  Installed the latest amd64 8.04 release candidate.
2)  Logged in.  Did a 'sudo apt-get install ubuntu-xen-server'.
3)  Checked the /etc/xen/xend-config.sxp to put in the network-bridge line, but it looked like it was already there and uncommented.
4)  Rebooted.
5)  Edited the /etc/xen-tools/xen-tools.conf to configure for my architecture (amd64), memory and disk size, network, and such.
6)  Ran 'xen-create-image --hostname=etch --ip=10.0.0.41 --ide --force'
7)  Ok.  'xm create -c etch.cfg' doesn't work here.  I had to go into /etc/xen/etch.cfg and change 'file:' to 'tap:aio:' for my disk.  And I had to add 'extra = "4 xencons=tty"' also so that I get a console (this doesn't seem to be necessary for a Hardy DomU install).
8)  Now that I've made those changes, run 'xm create -c etch.cfg'.  The server starts up and lets me log in.  But, while the VM claims that it has a 10.0.0.41 network, it doesn't seem to want to connect anywhere.

Doing a ifconfig on Dom0 gives

```
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:50:17:ea  
          inet addr:10.0.0.40  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe50:17ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74467049 (71.0 MB)  TX bytes:2761450 (2.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:784 (784.0 B)  TX bytes:784 (784.0 B)

peth0     Link encap:Ethernet  HWaddr 00:1f:d0:50:17:ea  
          inet6 addr: fe80::21f:d0ff:fe50:17ea/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:102183 errors:0 dropped:4769830593730 overruns:0 frame:0
          TX packets:34134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75917885 (72.4 MB)  TX bytes:2767378 (2.6 MB)
          Interrupt:18 Base address:0x6000 

vif5.0    Link encap:Ethernet  HWaddr fe:ff:ff:ff:ff:ff  
          inet6 addr: fe80::fcff:ffff:feff:ffff/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:73 overruns:0 carrier:0
          collisions:0 txqueuelen:32 
          RX bytes:280 (280.0 B)  TX bytes:12074 (11.7 KB)

```

...Any thoughts?  Might I be running into [https://bugs.launchpad.net/ubuntu/+source/xen-3.2/+bug/199533">bug 199533]("https://bugs.launchpad.net/ubuntu/+source/xen-3.2/+bug/199533">bug 199533")?  If so, given the comment at the end of that thread saying that the workaround doesn't work anymore with the latest kernel, is there anything that I can do?  

Or is there just something else that I've missed?

Thanks.

---

### Post by akpuf on 2008-04-24
Ok.  Turns out I was running into [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218126]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218126").  Installed the patch referred to in the bug and everything works well now.

Kind of sad that there are all these bugs in a released version, though.

---

### Post by agent8131 on 2008-04-24
Glad you were able to resolve the problem.  I'm waiting until 218126 is resolved before upgrading any DomU's to hardy.  I'd suggest that others consider doing the same.

---

