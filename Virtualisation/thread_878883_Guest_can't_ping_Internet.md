---
title: "Guest can't ping Internet"
date: 2008-08-03
forum: Virtualisation
---

### Post by satimis on 2008-08-03
Hi folks,


Ubuntu 6.06 server amd64 - guest
Ubuntu 8.04 server amd64 - host
KVM


Guest can run "apt-get update/upgrade" but unable to ping Internet/gateway/host, 100% package loss


$ telnet localhost 25```

Trying 127.0.0.1....
telnet: Unable to connect to remote host: Connection refused.

```


Guest;

$ cat /etc/network/interfaces```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```


$ ifconfig```

eth0	  Link encap:Ethernet  HWaddr 52:54:00:12:34:56
	  inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
	  inet6 addr: fe80::5054:ff:fe12:3456/64 Scope:Link
	  UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
	  RX packets:175 errors:0 dropped:0 overruns:0 frame:0
	  TX packets:249 errors:0 dropped:0 overruns:0 carrier:0
	  collisions:0 txqueuelen:1000
	  RX bytes:31829 (31.0 KiB)  TX bytes:31819 (31.0 KiB)
	  Interrupt:11 Base address:0x6000

lo	  Link encap:Local Loopback
	  inet addr:127.0.0.1  Mask:255.0.0.0
	  inet6 addr: ::1/128 Scope:Host
	  UP LOOPBACK RUNNING  MTU:16436  Metric:1
	  RX packets:41 errors:0 dropped:0 overruns:0 frame:0
	  TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
	  collisions:0 txqueuelen:0
	  RX bytes:3156 (3.0 KiB)  TX bytes:3156 (3.0 KiB)

```


Host;

$ cat /etc/network/interfaces```

auto lo
iface lo inet loopback


auto eth0
iface eth0 inet manual


# The primary network interface
auto br0
iface br0 inet static
        address 192.168.0.110
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

```


$ ifconfig```

br0       Link encap:Ethernet  HWaddr 00:0e:a6:f9:a3:5b
          inet addr:192.168.0.110  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fef9:a35b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85945 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3310146 (3.1 MB)  TX bytes:19758025 (18.8 MB)

eth0      Link encap:Ethernet  HWaddr 00:0e:a6:f9:a3:5b
          inet6 addr: fe80::20e:a6ff:fef9:a35b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4061600 (3.8 MB)  TX bytes:20372743 (19.4 MB)
          Interrupt:249 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7462 (7.2 KB)  TX bytes:7462 (7.2 KB)

vnet0     Link encap:Ethernet  HWaddr 4a:e2:d1:69:60:1b
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::48e2:d1ff:fe69:601b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

```


Please advise how to fix the problem.   TIA


Rmark: Iptables is NOT running


B.R.
satimis

---

### Post by igwk on 2008-08-04
Satimis, it looks like your guest is using user-mode networking, which does not allow guests to create ICMP packets as this requires root permissions.  It sounds like you want to use a TAP interface for your guest OS.  See [http://bellard.org/qemu/qemu-doc.html#SEC25](http://bellard.org/qemu/qemu-doc.html#SEC25) for more details about the networking options.  Also check out the "Network options" section of [http://bellard.org/qemu/qemu-doc.html#SEC10](http://bellard.org/qemu/qemu-doc.html#SEC10)

---

### Post by satimis on 2008-08-06
> **igwk said:**
> Satimis, it looks like your guest is using user-mode networking, which does not allow guests to create ICMP packets as this requires root permissions.  It sounds like you want to use a TAP interface for your guest OS.  See [http://bellard.org/qemu/qemu-doc.html#SEC25](http://bellard.org/qemu/qemu-doc.html#SEC25) for more details about the networking options.  Also check out the "Network options" section of [http://bellard.org/qemu/qemu-doc.html#SEC10](http://bellard.org/qemu/qemu-doc.html#SEC10)
Hi igwk,


Guest-1 Ubuntu6.06
Guest-2 Vista


I have been trying couple days without result.  It looks quite funny to me here.  Guest-1 can download packages on repo as well as on Internet but can't ping Internet.


Just installed Guest-2.  Vista can visit Internet without problem.


However another problem surfaces.  Each time I have to put the Vista installer on cdrom and run;

$ sudo kvm -hdb vista.img -cdrom /dev/scd0 -m 512 -boot d -vnc :1

to start vista.  The above command line was used to create vista.img.


If running;

$ sudo kvm vista.img -vnc :1

vista can't start just like running rescue CD asking me to select /safe-mode/normal-start/etc.  Non of the option can work.


Before wiping out KVM I'll try installing zimbra on Guest-1 to see what will happen


B.R.
satimis

---

