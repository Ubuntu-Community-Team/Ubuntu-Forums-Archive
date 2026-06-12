---
title: "Ubuntu ignoring Path MTU messages downstream"
date: 2014-08-26
forum: Server Platforms
---

### Post by mellowd on 2014-08-26
Hi. I have the following topology:

[U1] -------- [R1] -------- [R2] -------- [R3] -------- [U2]


All links have an MTU of 1500. I've been testing Path MTU Discovery with Ubuntu, and Ubuntu is ignoring a fragmentation needed packet if that ICMP doesn't come from it's local gateway. 

An example. U1 is directly connected to R1 with an MTU of 1500. U2 is a client requesting data via HTTP. PMTUD is on by default and so when U1 responds, that packet will have the DF-bit set in it's outgoing packets. Those packets will use the local MTU of 1500. If I drop the MTU between R1 and R2 and do the same thing, R1 will drop that packet and send an ICMP packet stating destination unreachable, fragmentation needed. That ICMP packet will also have the MTU of 1400 inside the packet. U1 then caches this information and reorignates packets with an MTU of 1400.

The above so far all works perfcectly fine. If I now push the R1-R2 link back up to MTU 1500 and drop the R2-R3 link to MTU 1400 it no longer works. R2 is dropping the packet and sending the ICMP packet as expected. Via tcpdump I can see U1 is receicing fragmentation needed packets from R2, but it's ignoring them. U1 is continuing to send packets with MTU 1500 onto the link. R2 is constantly dropping and informing U1. The result is U2 get no data at all.

If I reverse the server and client above, U2 acts on ICMP messages from R3, but ignores them from R2. Even though they are receiving those messages.


If I swap the servers with Windows 2012 servers, or Debian 7 servers, it works perfectly fine.

I've tried with both Ubuntu 14.04 and 13.10.

Clean install with apache2. Nothing else installed. No iptables rules.

Any ideas?

---

### Post by mellowd on 2014-08-26
Just a couple of things to add that I've just tested. To rule out anything in a newer kernel that could be causing this, I downgraded Ubuntu to 3.12 and upgraded Debian to kernel 3.12. Ubuntu still has the issue while Debian doesn't. 

There must be a 'feature' somewhere in Ubuntu that is causing it to ignore these messages when not received from the local router.

---

### Post by mellowd on 2014-08-27
More testing. Installed Ubuntu generic 3.14 kernel into Debian and Debian still works.

Removed apparmor from Ubuntu and it still doesn't work.

Do no-one have any ideas?

---

### Post by mellowd on 2014-08-28
Managed to figure this one out. Long explanation so I'll stick it on my blog and link it here in a few days

---

### Post by DigiAngel on 2014-08-30
This is EXACTLY the issue I was seeing with wired Windows devices and Windows Updates.  In June everything worked fine, then things went boom in July.  Pcaps showed the exact same thing....icmp frag needed.  My particular workaround was to put the device on wireless and it worked fine then.  And now this month eveything is working fine on the wire, so I have no idea what changed.  My last log shows several reboots, and I've made no configu changes so eh....I'll blame Microsoft :)

---

### Post by mellowd on 2014-09-02
In this case it's because Ubuntu has uRPF on by default and Debian has it off by default. Windows also has it off. More details here: [http://mellowd.co.uk/ccie/?p=5662](http://mellowd.co.uk/ccie/?p=5662)

---

### Post by DigiAngel on 2014-09-02
Great info...thank you and very nice blog :)

---

