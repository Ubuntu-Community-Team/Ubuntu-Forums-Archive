---
title: "KVM networking driving me batty"
date: 2009-03-25
forum: Virtualisation
---

### Post by freakalad on 2009-03-25
Hey guys,

Settled on KVM (as opposed to XenSource) as my VM solution (starting to ponder the wisdom of this move); both 64-bit at home (ibex) & at work (hardy).

Things at home seem OK at home (2 NIC's; pfSense router as VM), but here at work it's driving me up the wall.

Implemented steps as detailed in [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking) , where all nodes tap into br0 over eth0 onto local LAN.
Server is a-OK (sending this message from server), but clients are not able to see any other nodes on the greater LAN, other than other VM's on the same machine and the server/host.

This is my /etc/networking/interfaces:
```

auto  lo
iface lo inet loopback

###https://help.ubuntu.com/community/KVM/Networking

### eth0 ###
auto	eth0
iface	eth0 inet manual

auto	br0
iface 	br0 inet static

	address 10.0.0.16
	network 10.0.0.0
	netmask 255.255.255.0
	broadcast 10.0.0.255
	gateway 10.0.0.254

bridge_ports  eth0
bridge_fd     9
bridge_hello  2
bridge_maxage 12
bridge_stp    off

```

This is the status of my "sudo brctl show":
```

bridge name	bridge id		STP enabled	interfaces
br0		8000.001e8c91c378	no		eth0
							vnet0
							vnet1

```

& ifconfig:
```

br0       Link encap:Ethernet  HWaddr 00:1e:8c:91:c3:78  
          inet addr:10.0.0.16  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe91:c378/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4803448 (4.5 MB)  TX bytes:777603 (759.3 KB)

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:91:c3:78  
          inet6 addr: fe80::21e:8cff:fe91:c378/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4798614 (4.5 MB)  TX bytes:777743 (759.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9005043 (8.5 MB)  TX bytes:9005043 (8.5 MB)

vnet0     Link encap:Ethernet  HWaddr 00:ff:3d:c9:54:c4  
          inet6 addr: fe80::2ff:3dff:fec9:54c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:2052 (2.0 KB)  TX bytes:78955 (77.1 KB)

vnet1     Link encap:Ethernet  HWaddr 00:ff:d7:5e:bf:81  
          inet6 addr: fe80::2ff:d7ff:fe5e:bf81/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:4801 (4.6 KB)  TX bytes:69221 (67.5 KB)

```

"ps aux | grep vm" returns the following:
```

ps aux | grep vm
/usr/bin/kvm -M pc -m 512 -smp 1 -monitor pty -no-reboot -drive file=/home/jaco/Downloads/_lin_/_distros_/desktop/dsl-4.4.10.iso,if=ide,media=cdrom,boot=on -drive file=/home/jaco/vm/dsl.img,if=ide -net nic,macaddr=00:16:3e:75:f0:bb,vlan=0 -net tap,fd=12,script=,vlan=0 -usb -vnc 127.0.0.1:1
/usr/bin/kvm -M pc -m 512 -smp 1 -monitor pty -no-acpi -drive file=/home/jaco/vm/intrepid32.img,if=ide,boot=on -net nic,macaddr=00:16:3e:0d:cd:df,vlan=0 -net tap,fd=15,script=,vlan=0 -usb -vnc 127.0.0.1:2

```

The clients VM's, DSL & 32-bit Ibex, where defined & managed using virt-manager GUI (I like). Used to have firestarter installed (remove) & ufw is currently disabled, to I'm doubtful that it's IPTables.
This used to work, and still does at home, but now it doesn't, and for the love of me I cannot figure out why.

Could anyone please shed some light on the subject?
I'm sure it has to be a bit more than just a little common

Please advise

Thanks 

-J

---

### Post by freakalad on 2009-03-26
For some reason it's working now...hard to pint his one down.

---

