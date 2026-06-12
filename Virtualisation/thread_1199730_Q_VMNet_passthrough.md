---
title: "Q: VMNet passthrough"
date: 2009-06-29
forum: Virtualisation
---

### Post by grkuntzmd on 2009-06-29
I installed Ubuntu 9.04 x64 yesterday on my laptop. I am trying to run Windows XP (x86) as a guest in VMWare Workstation 6.5. I cannot get the NAT vmnet8 to work in Windows.

I installed Firestarter and told it that vmnet8 is my local network connect device and to enable internet connection sharing.

In the guest, I typed ipconfig/release and ipconfig/renew, but it cannot get an IP address from the DHCP server (keeps getting 169.x.x.x address). Of course, pinging yahoo.com doesn't work either.

If I do "ping 172.16.106.1" (the host address on vmnet1) in the guest, it pings fine.

Before people tell me to use VirtualBox instead, I cannot because of work policies.

Any ideas?

---

