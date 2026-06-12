---
title: "Ubuntu Server 16.04 slow boot with empty nics"
date: 2016-05-05
forum: Server Platforms
---

### Post by houstonbofh on 2016-05-05
I have several KVM servers running at various colos on 14.04, and I am starting to test 16.06...  All of my current servers have bridge utils on all nics.  A virtual firewall is installed and brings up the virtual network after booting.  This works fin on 14.04, but on 16.04 it hangs on boot for 5 minutes with "A start job is running for raise network interfaces (1 minutes of 5 mins 1 sec)" and just sits there...  How can I "Officer Bar Brady" it and tell it to "Move along, there is nothing to see here."  (So much for systemd speeding up boot times...  And do not get me started on the "Predictable Network Interface names" which already bit me once when I realized the nic was in a bad slot to ever unhook the Ethernet cables!)

Here is my interfaces file...
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary bridge

auto br0
iface br0 inet static
        bridge_ports enp3s0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0
	address 192.168.92.2
	netmask 255.255.255.0
	gateway 192.168.92.1
	dns-search mydomain.com
	dns-nameservers 192.168.92.1 8.8.8.8

# The secondary bridge

auto br1
iface br1 inet manual
        bridge_ports enp5s0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

# The tertiary bridge

auto br2
iface br2 inet dhcp
        bridge_ports ens4f0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

# The quaternary bridge
auto br3
iface br3 inet dhcp
        bridge_ports ens4f1
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```

---

### Post by ctm2 on 2016-05-07
I have a very similar situation with this, in trying to set up a xen hypervisor with 16.04 (everything works fine in 14.04 of course.  Same machine, same hardware, etc.

Firstly in reboot, I notice
```
[  OK  ] Started LXD - container startup/shutdown.[FAILED] Failed to start Raise network interfaces.
See 'systemctl status networking.service' for details.
[  OK  ] Reached target Network.

```

And the fun part (this is on remote console), I get the login prompt over and over again -- I can log in and stuff, but I keep getting the screen full of logins. In any case, when I run the suggested systemctl status, I get
```
systemctl status networking.service
Ubuntu 16.04 LTS xen-server ttyS0

(more login messages deleted)


&#9679; networking.service - Raise network interfaces
   Loaded: loaded (/lib/systemd/system/networking.service; enabled; vendor prese
  Drop-In: /run/systemd/generator/networking.service.d
           &#9492;&#9472;50-insserv.conf-$network.conf
   Active: failed (Result: timeout) since Fri 2016-05-06 21:00:26 PDT; 3min 52s 
     Docs: man:interfaces(5)
  Process: 1298 ExecStart=/sbin/ifup -a --read-environment (code=killed, signal=
  Process: 1287 ExecStartPre=/bin/sh -c [ "$CONFIGURE_INTERFACES" != "no" ] && [
 Main PID: 1298 (code=killed, signal=TERM)
    Tasks: 0 (limit: 512)
   Memory: 4.8M
      CPU: 51ms
   CGroup: /system.slice/networking.service


May 06 20:59:57 xen-server dhclient[1469]: DHCPDISCOVER on xenbr0 to
May 06 20:59:57 xen-server ifup[1298]: DHCPDISCOVER on xenbr0 to 255
May 06 21:00:06 xen-server dhclient[1469]: DHCPDISCOVER on xenbr0 to
May 06 21:00:06 xen-server ifup[1298]: DHCPDISCOVER on xenbr0 to 255
May 06 21:00:14 xen-server dhclient[1469]: DHCPDISCOVER on xenbr0 to
May 06 21:00:14 xen-server ifup[1298]: DHCPDISCOVER on xenbr0 to 255
May 06 21:00:26 xen-server systemd[1]: networking.service: Start ope
May 06 21:00:26 xen-server systemd[1]: Failed to start Raise network
May 06 21:00:26 xen-server systemd[1]: networking.service: Unit ente
lines 1-23
Ubuntu 16.04 LTS xen-server ttyS0
```

/etc/network/interfaces is
```
# for the xen hypervisor
auto lo
iface lo inet loopback


iface em1 inet manual


auto xenbr0
iface xenbr0 inet dhcp
    bridge_ports em1
```

Which of course worked for the xen in 14.04.  ifconfig is showing me basic settings for lo and xenbr0, but nothing for em1, which has me puzzled. Did 16.04 change this around? As I said, hardware is the same on this server which previously had xen on 14.04 w/o issues.



So clearly something's up? I will continue to post here if I find anything new or please if anyone else sees something going on. This is pretty much my first major dealings with systemd, so I'm not up on all that.

---

### Post by ctm2 on 2016-05-07
OK, I just fixed my own problem, but I don't know if it is related to yours. When I did an ifconfig -a (or alternatively, ip link show), it turns out all my NIC's had been renamed from em1 etc to eno1 and so on. Changing my interfaces file to the new names and rebooting fixed this problem. Now I have others (ha ha), but this one is okay. The issue for me turned out to be something "new" called "predictable interface names" which seems to have come along for the 16.04 ride (with systemd, I think). Fun!

---

### Post by houstonbofh on 2016-05-08
No, I had already programed around the (un)predictable interface names...  Don't get me started there! :)  This specifically is a slow boot and delay wait for a timeout.  I just want to set the timeout shorter.

---

### Post by houstonbofh on 2016-05-15
Found the answer thanks to senpai2 in this thread. [http://ubuntuforums.org/showthread.php?t=2323253&p=13489687#post13489687](http://ubuntuforums.org/showthread.php?t=2323253&p=13489687#post13489687)

Edit the timeout in /lib/systemd/system/networking.service and it is now a much faster boot!

---

