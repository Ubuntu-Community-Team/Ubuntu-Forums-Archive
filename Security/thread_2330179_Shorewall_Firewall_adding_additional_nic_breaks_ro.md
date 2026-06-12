---
title: "Shorewall Firewall adding additional nic breaks routing &amp; tcp"
date: 2016-07-09
forum: Security
---

### Post by pdeq on 2016-07-09
Hi,

I've looked and searched, but I can't seem to find what's going wrong.
Any help is appreciated.

I was doubting if this is the right forum, since this might be network related or firewall related, so please tell me if I should move this to an other place.

I'm running a 16.04 server on Vmware.
The server has currently 4 network cards, shorewall is installed and running fine.
However if I add a new additional network card, the problem starts.
The server is no longer routing any traffic, and from the console I can no longer reach an other device on the network.
The kern.log shows a lot of martians.

The new nic is detected properly, and show up in the ip link command.
/etc/network/interfaces looks OK, since each nic has their respective IP address, and can be pinged from the console with replies.
ip route looks fine.

At first i thought this might be shorewall, so I cleared it.
Iptables -L is clear, and default policies are in ACCEPT.
Nothing.....

Then I brought all (expect one) interface down (ifdown command)
The martians are gone now, but still I can't reach any device in the remaining subnet. 
 
What am i missing? I'm sure this will be something obvious, but I just can't find it.

Thx for your feedback.

Pascal

---

### Post by pdeq on 2016-07-09
Found it!!

Initially at system install, I had changed the default network naming (ens33) to the old “eth0” via grub. (see below) 

sed -i 's/^GRUB_CMDLINE_LINUX_DEFAULT=.*/GRUB_CMDLINE_LINUX_DEFAULT="net.ifnames=0"/' /etc/default/grub
sed -i 's/^GRUB_CMDLINE_LINUX=.*/GRUB_CMDLINE_LINUX="net.ifnames=0"/' /etc/default/grub
update-grub
reboot

If you add a new nic to your server, the assignment of eth0, eth1, etc... to the corresponding networkcard (MAC address) is no longer retained!
example: The device with MAC fc:98 was no longer assigned to eth1, but became eth3, eth2 became eth4, etc... !
Due to this routing & firewall rules were no longer working as expected.

I doubt this is expected behavior?

---

