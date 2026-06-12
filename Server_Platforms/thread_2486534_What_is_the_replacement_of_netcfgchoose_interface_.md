---
title: "What is the replacement of netcfg/choose_interface for Ubuntu autoinstall?"
date: 2023-05-03
forum: Server Platforms
---

### Post by actatux on 2023-05-03
Hello,

I have been searching for the past two hours but could not find any relevant documentation to select the network interface for server installation through PXE. Before 22.04, I was using preseed and the Debian installer to install Ubuntu. It was possible to select the network interface with `netcfg/choose_interface=enp5s0f0`.

On a new server with several network interfaces, the installer fails:
```

Internet Systems Consortium DHCP Client 4.4.1
Copyright 2004-2018 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/


Listening on LPF/enp5s0f1/3c:ec:ef:ab:84:71
Sending on   LPF/enp5s0f1/3c:ec:ef:ab:84:71
Listening on LPF/enp5s0f0/3c:ec:ef:ab:84:70
Sending on   LPF/enp5s0f0/3c:ec:ef:ab:84:70
Listening on LPF/enxb03af2b6059f/b0:3a:f2:b6:05:9f
Sending on   LPF/enxb03af2b6059f/b0:3a:f2:b6:05:9f
Sending on   Socket/fallback
DHCPDISCOVER on enp5s0f1 to 255.255.255.255 port 67 interval 3 (xid=0x62bfe01)
DHCPDISCOVER on enp5s0f0 to 255.255.255.255 port 67 interval 3 (xid=0x6491ed53)
DHCPDISCOVER on enxb03af2b6059f to 255.255.255.255 port 67 interval 3 (xid=0x175fc50d)
DHCPOFFER of 169.254.3.1 from 169.254.3.254
DHCPREQUEST for 169.254.3.1 on enxb03af2b6059f to 255.255.255.255 port 67 (xid=0xdc55f17)
DHCPACK of 169.254.3.1 from 169.254.3.254 (xid=0x175fc50d)
bound to 169.254.3.1 -- renewal in 385886 seconds.
no search or nameservers found in /run/net-enxb03af2b6059f.conf /run/net-enxb03af2b6059f.conf /run/net6-*.conf
Begin: Running /scripts/casper-premount ... done.
done.
Begin: Trying netboot from : ... Begin: Trying to download and mount http://mirror.example.tld/mirror/iso/ubuntu-22.04.2-live-server-amd64.iso ... wget: bad address 'mirror.example.tld'
done.
Unable to find a live file system on the network
[   77.075801] ixgbe 0000:05:00.0 enp5s0f0: NIC Link is Up 10 Gbps, Flow Control: None
[   77.093974] IPv6: ADDRCONF(NETDEV_CHANGE): enp5s0f0: link becomes ready


(initramfs) cat /proc/cmdline 
BOOT_IMAGE=/images/ubuntu-22.04/vmlinuz console=tty0 console=ttyS1,115200 iommu=pt autoinstall ip=dhcp cloud-config-url=/dev/null url=http://mirror.example.tld/mirror/iso/ubuntu-22.04.2-live-server-amd64.iso ds=nocloud-net;s=http://172.16.2.8/cblr/svc/op/autoinstall/system/dn/ ethdevice-timeout=30 live-netdev=enp5s0f0
(initramfs) ip a
1: lo: <LOOPBACK> mtu 65536 qdisc noop qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enxb03af2b6059f: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether b0:3a:f2:b6:05:9f brd ff:ff:ff:ff:ff:ff
    inet 169.254.3.1/24 brd 169.254.3.255 scope global enxb03af2b6059f
       valid_lft forever preferred_lft forever
    inet6 fe80::b23a:f2ff:feb6:59f/64 scope link 
       valid_lft forever preferred_lft forever
3: enp5s0f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq qlen 1000
    link/ether 3c:ec:ef:ab:84:70 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::3eec:efff:feab:8470/64 scope link 
       valid_lft forever preferred_lft forever
4: enp5s0f1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq qlen 1000
    link/ether 3c:ec:ef:ab:84:71 brd ff:ff:ff:ff:ff:ff


```

The PXE boot file is:
```

cobbler:~$ cat /srv/tftp/grub/system/3c:ec:ef:ab:84:70
set system="dn-b001"
set timeout=1
set default='dn-b001'
menuentry 'dn-b001' --class gnu-linux --class gnu --class os {
  echo 'Loading kernel ...'
  clinux /images/ubuntu-22.04/vmlinuz  console=tty0 console=ttyS1,115200 iommu=pt autoinstall ip=dhcp cloud-config-url=/dev/null url=http://mirror.example.tld/mirror/iso/ubuntu-22.04.2-live-server-amd64.iso "ds=nocloud-net;s=http://192.168.0.8/cblr/svc/op/autoinstall/system/dn/" ethdevice-timeout=30 live-netdev=enp5s0f0
  echo 'Loading initial ramdisk ...'
  cinitrd /images/ubuntu-22.04/initrd
  echo '...done'
}
```

Do you know where I could find appropriate documentation to select the network interface with the new Ubuntu installer?

---

### Post by actatux on 2023-09-01
Looks like nobody knows :D

---

### Post by MAFoElffen on 2023-09-02
Do you mean like this?
```

cat > /var/lib/tftpboot/meta-data <<EOF
instance-id: focal-autoinstall
EOF

cat > /var/lib/tftpboot/user-data <<'EOF'
#cloud-config
autoinstall:
  version: 1
  # use interactive-sections to avoid an automatic reboot
  #interactive-sections:
  #  - locale
  apt:
    # even set to no/false, geoip lookup still happens
    #geoip: no
    preserve_sources_list: false
    primary:
    - arches: [amd64, i386]
      uri: http://us.archive.ubuntu.com/ubuntu
    - arches: [default]
      uri: http://ports.ubuntu.com/ubuntu-ports
  # r00tme
  identity: {hostname: focal-autoinstall, password: $6$.c38i4RIqZeF4RtR$hRu2RFep/.6DziHLnRqGOEImb15JT2i.K/F9ojBkK/79zqY30Ll2/xx6QClQfdelLe.ZjpeVYfE8xBBcyLspa/,
    username: ubuntu}
  keyboard: {layout: us, variant: ''}
  locale: en_US.UTF-8
  # interface name will probably be different
  network:
    network:
      version: 2
      ethernets:
        ens192:
          critical: true
          dhcp-identifier: mac
          dhcp4: true
  ssh:
    allow-pw: true
    authorized-keys: []
    install-server: true
  # this creates an efi par

```

---

### Post by actatux on 2023-11-27
Well, I'm not sure this would work since the initrd does not get a DHCP lease on the correct interface. I can't even download the ISO from the server. I thought the ISO would boot the installer and use the cloud-init files user-data and meta-data.

Anyway, I will give it a try.

---

### Post by actatux on 2023-11-27
Yeah, same behaviour. The initrd still enumerate all the interfaces and get a lease from the wrong one.

```

#cloud-config
autoinstall:
[...]
  storage:
    swap:
      size: 0
    layout:
      name: lvm
      match:
        size: smallest
  network:
    network:
      version: 2
      ethernets:
        eno8303:
          critical: true
          dhcp-identifier: mac
          dhcp4: true
[...]

```

At boot:
```

Listening on LPF/idrac/ec:2a:72:1c:9b:89
Sending on   LPF/idrac/ec:2a:72:1c:9b:89
Listening on LPF/eno8403/ec:2a:72:10:6a:df
Sending on   LPF/eno8403/ec:2a:72:10:6a:df
Listening on LPF/eno8303/ec:2a:72:10:6a:de
Sending on   LPF/eno8303/ec:2a:72:10:6a:de
Listening on LPF/eno12409np1/14:23:f2:30:5f:c1
Sending on   LPF/eno12409np1/14:23:f2:30:5f:c1
Listening on LPF/eno12399np0/14:23:f2:30:5f:c0
Sending on   LPF/eno12399np0/14:23:f2:30:5f:c0
Sending on   Socket/fallback
DHCPDISCOVER on idrac to 255.255.255.255 port 67 interval 3 (xid=0x65b26645)
DHCPDISCOVER on eno8403 to 255.255.255.255 port 67 interval 3 (xid=0xf4c21857)
DHCPDISCOVER on eno8303 to 255.255.255.255 port 67 interval 3 (xid=0x9e0dea23)
DHCPDISCOVER on eno12409np1 to 255.255.255.255 port 67 interval 3 (xid=0x7838236c)
DHCPDISCOVER on eno12399np0 to 255.255.255.255 port 67 interval 3 (xid=0xc65db310)




BusyBox v1.30.1 (Ubuntu 1:1.30.1-7ubuntu3) built-in shell (ash)
Enter 'help' for a list of built-in commands.


(initramfs) DHCPOFFER of 169.254.1.2 from 169.254.1.1
DHCPREQUEST for 169.254.1.2 on idrac to 255.255.255.255 port 67 (xid=0x4566b265)
DHCPACK of 169.254.1.2 from 169.254.1.1 (xid=0x65b26645)
bound to 169.254.1.2 -- renewal in 375432 seconds.
no search or nameservers found in /run/net-idrac.conf /run/net-idrac.conf /run/net6-*.conf
Begin: Running /scripts/casper-premount ... done.
done.
Begin: Trying netboot from : ... Begin: Trying to download and mount http://mymirror/iso/ubuntu-22.04.3-live-server-amd64.iso ... wget: bad address 'mymirror'
done.
Unable to find a live file system on the network

```

---

### Post by actatux on 2023-11-27
Answer: use `BOOTIF` in the boot command line.

```

$ sudo cat /srv/tftp/grub/system/ec:2a:72:10:6a:de
set system="myhost"
set timeout=1
set default='myhost'
menuentry 'myhost' --class gnu-linux --class gnu --class os {
  echo 'Loading kernel ...'
  clinux /images/ubuntu-22.04.3/vmlinuz  autoinstall ip=dhcp cloud-config-url=/dev/null url=http://mymirror/iso/ubuntu-22.04.3-live-server-amd64.iso console=tty0 console=ttyS0,115200 iommu=pt nvme-core.multipath=N "ds=nocloud-net;s=http://cobbler/cblr/svc/op/autoinstall/system/myhost/" BOOTIF=01-ec:2a:72:10:6a:de
  echo 'Loading initial ramdisk ...'
  cinitrd /images/ubuntu-22.04.3/initrd
  echo '...done'
}

```

---

### Post by MAFoElffen on 2023-11-28
So this is solved now? Happy to see you got that gong for you.

If solved, please visit the "Thread Tools" link in the upper left of this page to mark your thread as "Solved" so that others may find what worked for you.

---

