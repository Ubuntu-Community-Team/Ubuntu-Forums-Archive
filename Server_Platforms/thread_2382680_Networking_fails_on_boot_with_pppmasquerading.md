---
title: "Networking fails on boot with ppp/masquerading"
date: 2018-01-16
forum: Server Platforms
---

### Post by chris413 on 2018-01-16
Hi.

I am running Ubuntu 16.04. I have 2 network cards enp2s0 /enp3s0. enp2s0 points to the lan with a fixed IP and enp3s0 is connected to a DSL modem. I used pppoeconf to configure the DSL and UFW does the NAT/Masquerading.
On boot I get the following error. (although in ifconfig the interfaces show up and masquerading is working). Could someone be so kind and point me towards where I went wrong?

Thanks, Chris


&#9679; networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor preset: enabled)
  Drop-In: /run/systemd/generator/networking.service.d
           &#9492;&#9472;50-insserv.conf-$network.conf
   Active: failed (Result: exit-code) since Di 2018-01-16 13:41:54 CET; 1min 20s ago
     Docs: man:interfaces(5)
  Process: 1306 ExecStart=/sbin/ifup -a --read-environment (code=exited, status=1/FAILURE)
  Process: 1120 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [ -n "$(ifquery --read-environment --list --exclude=lo)" ] && udevadm settle (code=exited, status=0/SUCCESS)
 Main PID: 1306 (code=exited, status=1/FAILURE)

Jan 16 13:41:54 studio pppd[1404]: PPP session is 866
Jan 16 13:41:54 studio pppd[1404]: Connected to 7e:e2:ca:be:08:b0 via interface enp3s0
Jan 16 13:41:54 studio pppd[1404]: Using interface ppp0
Jan 16 13:41:54 studio pppd[1404]: Connect: ppp0 <--> enp3s0
Jan 16 13:41:54 studio pppd[1404]: Terminating on signal 15
Jan 16 13:41:54 studio pppd[1404]: Connection terminated.
Jan 16 13:41:54 studio pppd[1404]: Failed to disconnect PPPoE socket: 114 Operation already in progress
Jan 16 13:41:54 studio systemd[1]: Failed to start Raise network interfaces.
Jan 16 13:41:54 studio systemd[1]: networking.service: Unit entered failed state.
Jan 16 13:41:54 studio systemd[1]: networking.service: Failed with result 'exit-code'.

---

### Post by chris413 on 2018-01-17
Problem solved. 

Flush all network adapters and restart networking.
sudo ip addr flush dev enp2s0 && sudo ip addr flush dev enp3s0 && sudo ip addr flush dev ppp0 && sudo systemctl restart networking.service

---

### Post by troffasky on 2018-05-30
Did this actually solve the issue with ppp0 staying up on boot? It looks like all you've done is restart networking.

---

### Post by darkod on 2018-05-31
I would recommend getting rid of ufw as soon as possible and using plain iptables. Much cleaner and better solution.

---

