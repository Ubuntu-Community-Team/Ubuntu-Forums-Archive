---
title: "ssh connection problem"
date: 2008-08-14
forum: Server Platforms
---

### Post by satimis on 2008-08-14
Hi folks,


Server (Virtual Machine)
Host - Ubunutu 8.04 desktop amd64
router IP 192.168.0.110

/etc/network/interfaces```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
address 192.168.0.110
netmask 255.255.255.0
gateway 192.168.0.1
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

```

Iptables is not running

$ sudo iptables -L```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

```


Local PC
OS - Ubuntu 6.06
router IP 192.168.0.52


Local terminal:-
$ ssh 192.168.0.110```

ssh: connect to host 192.168.0.110 port 22: Connection refused

```


Server terminal:-

$ tail /var/log/messages```

Aug 15 00:01:42 ubuntu804-desktop kernel: [53629.293679] sd 13:0:0:0: [sdb] Write Protect is off
Aug 15 00:01:42 ubuntu804-desktop kernel: [53629.297822] sd 13:0:0:0: [sdb] 20010816 512-byte hardware sectors (10246 MB)
Aug 15 00:01:42 ubuntu804-desktop kernel: [53629.300684] sd 13:0:0:0: [sdb] Write Protect is off
Aug 15 00:01:42 ubuntu804-desktop kernel: [53629.300695]  sdb: sdb1 sdb2
Aug 15 00:01:42 ubuntu804-desktop kernel: [53629.320123] sd 13:0:0:0: [sdb] Attached SCSI disk
Aug 15 00:01:42 ubuntu804-desktop kernel: [53629.320162] sd 13:0:0:0: Attached scsi generic sg2 type 0
Aug 15 00:01:42 ubuntu804-desktop kernel: [53630.120523] kjournald starting.  Commit interval 5 seconds
Aug 15 00:01:42 ubuntu804-desktop kernel: [53630.154669] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Aug 15 00:01:42 ubuntu804-desktop kernel: [53630.156768] EXT3 FS on sdb2, internal journal
Aug 15 00:01:42 ubuntu804-desktop kernel: [53630.156774] EXT3-fs: mounted filesystem with ordered data

```


$ tail /var/log/syslog```

Aug 15 00:01:42 ubuntu804-desktop NetworkManager: <debug> [1218729702.189302] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_121F43BC2222_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug 15 00:01:42 ubuntu804-desktop NetworkManager: <debug> [1218729702.313023] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Maxtor_9_1021U2_121F43BC2222_0_0'). 
Aug 15 00:01:42 ubuntu804-desktop NetworkManager: <debug> [1218729702.694560] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_348D_1549'). 
Aug 15 00:01:42 ubuntu804-desktop NetworkManager: <debug> [1218729702.800859] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_a8b80721_b3c0_4de7_8f0d_8eba9ae275dc'). 
Aug 15 00:01:42 ubuntu804-desktop hald: mounted /dev/sdb1 on behalf of uid 1000
Aug 15 00:01:42 ubuntu804-desktop kernel: [53630.120523] kjournald starting.  Commit interval 5 seconds
Aug 15 00:01:42 ubuntu804-desktop kernel: [53630.154669] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Aug 15 00:01:42 ubuntu804-desktop kernel: [53630.156768] EXT3 FS on sdb2, internal journal
Aug 15 00:01:42 ubuntu804-desktop kernel: [53630.156774] EXT3-fs: mounted filesystem with ordered data mode.
Aug 15 00:01:42 ubuntu804-desktop hald: mounted /dev/sdb2 on behalf of uid 1000

```


# find / -name ssh```

/etc/ssh
/usr/bin/ssh
/usr/lib/apt/methods/ssh
find: /home/satimis/.gvfs: Permission denied
/tmp/keyring-LIVkk9/ssh

```

# ls -l /tmp/keyring-LIVkk9/```

total 0
srwxr-xr-x 1 satimis satimis 0 2008-08-14 13:04 socket
srwxr-xr-x 1 satimis satimis 0 2008-08-14 13:04 socket.pkcs11
srwxr-xr-x 1 satimis satimis 0 2008-08-14 13:04 ssh

```


Please advise where shall I check and how to fix the problem.  TIA


B.R.
satimis

---

### Post by windependence on 2008-08-14
I'm not sure I understand what the problem IS. Where are you trying to ssh from and to? Also this probably has nothing to do with that but your router IP is 192.168.0.52, and you have the gateway as 192.168.0.1. Usually, the gateway and router address are the same.

-Tim

---

### Post by satimis on 2008-08-14
Hi Tim,


> 
Where are you trying to ssh from and to? 

From local PC of router IP-192.168.0.52 ssh connect the Server (router IP-192.168.0.110)


The other way round has no problem.  The server (host OS) can ssh connect local PC.

$ ssh -p 2222 192.168.0.52
works seamlessly.


B.R.
satimis

---

### Post by satimis on 2008-08-14
Hi Tim,


I forgot installing openssh-server.

Problem solved after installing openssh-server on Ubuntu 8.04 desktop

Thanks


B.R.
satimis

---

