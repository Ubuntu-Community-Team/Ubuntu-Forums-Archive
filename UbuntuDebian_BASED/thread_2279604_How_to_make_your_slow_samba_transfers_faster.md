---
title: "How to make your slow samba transfers faster"
date: 2015-05-24
forum: Ubuntu/Debian BASED
---

### Post by Linux90's on 2015-05-24
This was done with debian jessie but is relevant obviously, to ubuntu and made a MASSIVE difference.

when transferring files from a win7 box to the linux nas the speed was slow, by default ~20MB/s.
transfers to the same machine running freenas were around the 10-12MB range.
after tweaking and restarting the smbd daemon, the rate went up to ~112MB according to the details in the win7 transfer
dialog window.

since the box is a backup machine, having a max network utilization of ~90% is the most i would like to leave it at.
if you do go for 95%+ utilization, this will affect any surfing/downloading/streaming in a very detrimental manner.
i was transferring data around the 80% utilization mark and watching a youtube video at 1080p HD at the same time and suffered 
no video loss

check that jumbo frames are enabled for all nic's if they support it:

the MTU is 1500 default when seen using ifconfig
change to 9000 by editing /etc/network/interfaces
you just need to add "mtu 9000"
on the line beneath your nic declaration
this change is permanent but will require setting up a static address

remember!!! your hardware must support jumbo frames or this can/will cause problems/lag.
if your hardware only supports 7k frames or 4k frames, set the value accordingly, also, both communicating
nic's should have the same jumbo frame settings for best performance/compatibility however, test your setup,
there are far too many hardware connotations to apply any rule across, ymmv.

the most important part is in the samba settings (version 4.x).



set the samba socket options to increase transfer speeds.
this can be done either directly to the smb.conf file, or using a gui, eg. GADMIN-SAMBA


socket options = TCP_NODELAY SO_RCVBUF=524288 SO_SNDBUF=524288 IPTOS_LOWDELAY 

the greatest increase came from setting the SO_RCVBUF and SO_SNDBUF
the default buffers were 8192
changes resulted in the following speed changes:

buffer size    speed        network
                utilization
524288     ->     100MB+        ~90%
262144     ->      55MB        ~50%
65536    ->    ~40MB        ~40%
8192    ->    ~20MB        ~20%

obviously, small transfers are slower anyway, between 1% and 40% network utlization
the larger files hit ~90% without issue

the nic's on the network are Gigabit nic's, the cables are cat5e or cat6
the switches and routers on the network are gigabit capable.

if this information helps you, give it a like/commend

gd luck 

:)

(not new here, but had to create a new account for the SSO thing)

---

### Post by howefield on 2015-05-24
Thread moved to the *"Ubuntu/Debian BASED"* forum.

---

### Post by Daniel_Viera on 2016-03-22
Works fine!!
Tks

---

