---
title: "Duplicate network address/device reported in Windows 10 VirtualBox guest's AV/FW"
date: 2017-11-07
forum: Virtualisation
---

### Post by accounts0 on 2017-11-07
Haven't been able to get a screenshot yet, will update/edit this thread with it once I'm able.

The error message comes from ESET Internet Security's Firewall component & disappears a few seconds after login. When I map the network there appear [1] to be 3 devices all with the same IP but different MAC addresses. The guest has a primary, NAT'd interface. The affected network is the Host-Only interface I use to RDP in.

Not sure how to sort this. Could use a hand. Thanks.


[1]
[https://imgur.com/a/EL8L4](https://imgur.com/a/EL8L4)

---

### Post by wildmanne39 on 2017-11-07
*Thread moved to **Virtualisation for a better fit **.*

---

### Post by accounts0 on 2017-11-07
I've spent the last few hours re-installing both the guest VM's network adapters, as well as the ESET Internet Security package. And reconfiguring it all slowly & methidically to be sure all is as proper as I can get it.

I've done away with the guest's primary network interface being what Virtualbox calls a 'NAT Network', & opted instead for the default 'NAT' network, which appears to be the same but doesn't involve a named entry in the application's network management dialog. The 'Host-Only' network remained necessary so it's been reestablished. Their IP & MAC addresses have all changed, but are still RHEL para-virtualized.

I wasn't able to get the second, 'Host-Only' network to permanently switch to a 'Private' & remains a 'Public' network to Windows. Spent >2 hours fighting & gave up. Afterward I found that if I were to enter an incoming RDP rule directly into Windows' Advanced Firewall dialog its values would apply to both network types instead of adding the entry via the easier interface where it wanted to have either (or both) 'Private' & 'Public' network types' boxes checked, so it seemed almost moot at the end, but it still bothers me a bit that it's not absolutely proper. Whatever- it's nested in the laptop anyway, I don't know why I care, a bit of OCD perhaps, :-)

At one point I was getting 2 errors upon RDP'ing in, that the ESET firewall blocked. It was something about both a duplicate IP address on the network and also an ARP cache attack. After I clicked something to the effect of 'Don't bother me again for this' button which created an exception, I un-did it so I could re-create it & get screenshots to post here. But when I tried it didn't happen the same anymore. Now I just have the 'Duplicate IP address on network' error, but nothing about ARP & nothing's blocked outright, just a warning- that I eventually made an exception for as well just in case it decides to block later. Screenshots [1]. I don't know what I did differently, I expected it to re-appear like it had that first time- oh, well.

Apparently this IP address duplication thing is something VirtualBox does on a consistent basis, since it happened again now after having rebuilt the whole network. Would like to understand better what exactly is happening with it.

[1]
[https://imgur.com/a/O1KR8](https://imgur.com/a/O1KR8)

---

### Post by accounts0 on 2017-12-13
Switched to bridged network connections on both wired & wireless interfaces, so the VM has 1 of each & either will be working at a time. Seems to have solved it.

---

