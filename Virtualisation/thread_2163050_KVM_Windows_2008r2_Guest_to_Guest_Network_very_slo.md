---
title: "KVM Windows 2008r2 Guest to Guest Network very slow on same host."
date: 2013-07-16
forum: Virtualisation
---

### Post by atomicmongoose on 2013-07-16
KVM Windows 2008r2 Guest to Guest Network very slow on same host.

 

 I have 4 Recently updated  12.04 KVM hosts with a variety of hardware.   All of them have a similar issue when two windows Guests  2008 or Windows 7 VM's have to talk to each other.
 

 Dell 410, 710, 810 ancient Dell t3400 workstation, and an old HP gl600, all exhibit the same problem and return similar results in the below tests.  Some machines have 12 cores and 64G of ram in an LVM raid-10, the slower old ones have 4 cores and 8G of memory.  But as mentioned above all exhibit the same issues.
 

 All hosts dist-upgraded as of yesterday, all the Windows machines use both e1000 or Virtio (latest) with little improvement.   
 

 I use openvswitch for bridging mostly because bonding of physical nics works so much better than without.   
 

 Using iperf for my testing:
 

 -As a basis of comparison, a linux VM (also 12.04)  will communicate wonderfully to another Ubuntu host or to another Ubuntu VM.     
 

 -iperf in the Ubuntu/vm or host  to Ubuntu/vm or host scenario averages 11Gbit/s  Sometimes as high as 16Gbit/s    
 

 

 -Windows7/2008 to Windows7/2008  without any registry tweaking or after a reboot averages  12Mbit/s   
 

 -Windows7/2008 to host is slightly better at 200Mbit/s   
 

 -If I disable TSO on the host nics/bridges and disable any offloading in the Windows Adapters, and if the stars and properly aligned, I have been able to average the iperf test up to 120Mbit/s between a win7/2008 machines.
 

 -the registry "tweaks" are issued via netsh commands  (From various places that recommend this for KVM and VMware)  Haven't figured out which are the most magical of the following.
 

 ```
netsh int tcp set global rss=disabled

 netsh int tcp set global autotuning=disabled
 netsh int tcp set global netdma=disabled
 netsh int tcp set global chimney=disabled
 netsh int tcp set global congestionprovider=ctcp

``` 

 On the host
 ```
ethtool -K eth0 tso off

 ethtool -K eth1 tso off
 ethtool -K br0 tso off

``` 

 -A reboot of the host seems to reset me back to 12Mbit average.      
 

 -I use Virtio for disk drives, those all seem to run about as well as I can expect.  No issues there.
 

 -Added vhost_net to /etc/modules (not sure if that does anything)
 

 Maybe it's just me but I assume I should at least be getting close to 1Gbit on my VM's.   
 

 Can anyone else provide some metrics on what they get between two guests on the same host?
 

 

 Any ideas at all to try?

---

### Post by atomicmongoose on 2013-07-17
No thoughts or benchmarks from anyone else?

Any thoughts on where else I should ask the question?

---

### Post by atomicmongoose on 2013-07-19
Hate to bump my own thread...

Been trying all sorts of tweaks and fiddlings with little result.


At this point I really need some metrics to compare to. 

So!  if you have two or more Windows VMs on a host.   Move a large file between them for me, how fast did it go?

Or, if you would grab a copy of iperf (free) and run a test between the two, that would be fabulous.  Thanks for your help

---

