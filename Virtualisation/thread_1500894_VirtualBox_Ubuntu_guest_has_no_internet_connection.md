---
title: "VirtualBox Ubuntu guest has no internet connection"
date: 2010-06-03
forum: Virtualisation
---

### Post by xefix on 2010-06-03
Hi, all

I'm new to VirtualBox and Linux, so I've run into a bit of trouble trying to set up an internet connection. My host is Windows XP, and my guest is Ubuntu 10.04. I am attempting to connect using NAT (I need simple internet access for browsing web pages and downloading/updating packages), though I have tried other types of connections and none have worked. I am using version 3.2.0 of VirtualBox, so a lot of instructions that I've found online don't apply to me because they are for slightly older versions. The official VirtualBox guide hasn't been helpful either because it says that NAT is supposed to work without any set up, but it doesn't, in my case.
I've been able to ping both the host and the guest, but not any outside IPs or web addresses.
I don't really know what other information to provide - please let me know. Also, I know almost nothing when it comes to networks, so please be specific! Thank you!

NOTE: I am reposting this thread as I did not previously realize there was a whole forum for virtualization.

---

### Post by mikewhatever on 2010-06-03
Check the Windows firewall settings. Has virtualbox been allowed internet access?

---

### Post by xefix on 2010-06-03
I have just explicitly set the firewall to allow all traffic to and from VirtualBox, but internet is still not working in my guest os. More specifically, Ubuntu says that it is connected to eth4, but I am not exactly sure what that is. The internet connection my host has is wireless.

---

### Post by mikewhatever on 2010-06-03
Well, eth4 is a networking interface. Try running **ifconfig** to see if you get an IP address in Ubuntu.

---

### Post by xefix on 2010-06-03
Here's the entire output of ifconfig:

eth4      Link encap:Ethernet  HWaddr 08:00:27:35:9a:73  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe35:9a73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32354 (32.3 KB)  TX bytes:23699 (23.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by drdos2006 on 2010-06-03
Your guest operating system needs your network connection to be bridged, not NAT from Virtualbox Settings.

regards

---

### Post by xefix on 2010-06-03
When I change the settings to use a bridged connection and attempt to connect to eth4 after loading Ubuntu, it tries to connect for a while and fails, even though eth4 is in the list of available networks. I've tried a bunch of different adapter types from the VirtualBox menu as well...

---

### Post by mikewhatever on 2010-06-03
> **drdos2006 said:**
> Your guest operating system needs your network connection to be bridged, not NAT from Virtualbox Settings.

regards

That's not essential. I usually stick with the default, NAT, but tried the other one as well.

xefix, try ping your Windows machine from Ubuntu:
ping -c5 windows-ip-whatever-it-is

try pinging google.com
ping -c5 66.102.9.147

---

### Post by xefix on 2010-06-04
Problem solved, everyone. I was having this issue at work, but everything was fine when I got home. It probably was a firewall issue all along - not my personal firewall, but the company one. Thanks!
(now for the fun part - getting this straightened out with IT!)

---

### Post by kavoura on 2010-06-24
I am having the same problem, but for me it is a random problem. Sometimes the guest Ubuntu 10.04 system has a network connection, sometimes not.
The host is Ubuntu 9.04. Both are 64-bit OS.
The host has a network connection, can access the Internet okay, but the guest will sometimes just lose the connection for no apparent reason.
I have tried both NAT and bridged networking from the VirtualBox settings, and NAT has so far given me more connections.
I cannot find any decent networking tools in Ubuntu to help me. I used to use Windows XP and its predecessors, but had way too many problems, so I went for Linux instead. But networking, IMO, was far easier to set up in Windows than it is in Ubuntu.

---

### Post by kavoura on 2010-06-24
I can also run Easy Peasy 1.6 on Virtual Box, which is based on Ubuntu 10.04, and the networking in that works okay. It seems to have the same settings as Ubuntu 10.04.

In Easy Peasy, I notice that the network connection icon is 2 arrows, but in my Ubuntu guest it is more like a wireless network symbol. I have no wireless networking, just wired. Maybe Ubuntu sees the wired connection as a wireless and cannot configure it properly?

---

