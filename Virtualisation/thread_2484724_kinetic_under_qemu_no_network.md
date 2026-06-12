---
title: "kinetic under qemu no network"
date: 2023-03-07
forum: Virtualisation
---

### Post by jusp on 2023-03-07
I am trying to get an arm linux running under qemu on my x86 host following the instructions in [https://wiki.ubuntu.com/ARM64/QEMU](https://wiki.ubuntu.com/ARM64/QEMU).
This works, except that I appear to get no network connection. Both my host and my guest are Ubuntu 22.10 (kinetic). What could I be doing wrong?

The following command is used to start qemu:
 ```
sudo qemu-system-aarch64 -m 1024 -cpu cortex-a57 -M virt -nographic -pflash /usr/share/AAVMF/AAVMF_CODE.fd -pflash flash1.img -drive if=none,file=kinetic-server-cloudimg-arm64.img,id=hd0 -drive file=user-data.img,format=raw  -device virtio-blk-device,drive=hd0 -netdev type=tap,id=net0 -device virtio-net-device,netdev=net0,mac=00:16:3e:5a:fa:54 
```
This command starts running with an error W: /etc/qemu-ifup: no bridge for guest interface found.

sudo sh /etc/qemu-ifup tap0

```
$ sudo sh /etc/qemu-ifup tap0
W: /etc/qemu-ifup: no bridge for guest interface found

```
```
$ ifconfig
enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.14  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::4eed:b0a0:bfd4:a9bd  prefixlen 64  scopeid 0x20<link>
        ether 9c:8e:99:ee:59:cb  txqueuelen 1000  (Ethernet)
        RX packets 486  bytes 161945 (161.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 647  bytes 83595 (83.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5270  bytes 582511 (582.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5270  bytes 582511 (582.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

tap0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::9469:b5ff:fe40:bcdf  prefixlen 64  scopeid 0x20<link>
        ether 96:69:b5:40:bc:df  txqueuelen 1000  (Ethernet)
        RX packets 2  bytes 164 (164.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 21  bytes 2627 (2.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:48:be:c8  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
```
$ cat user-data
#cloud-config
password: XXXXXXX
chpasswd: { expire: False }
ssh_pwauth: True
```

---

### Post by jusp on 2023-03-08
Ah, learning fast here. It appeared I had to create a bridge,

See 
  [https://ubuntu.com/server/docs/network-configuration](https://ubuntu.com/server/docs/network-configuration)
  [https://askubuntu.com/questions/1257461/error-in-network-definition-bond0-interface-eno2-is-not-defined](https://askubuntu.com/questions/1257461/error-in-network-definition-bond0-interface-eno2-is-not-defined)

Things are running now..

---

### Post by MAFoElffen on 2023-03-08
Also... If you are a member of groups kvm & libvirt, then you can start qemu-system-ARCH without having to use sudo.

---

### Post by DuckHook on 2023-03-08
Welcome to the forums, jusp.

A useful hint:

Are you running a GUI environment? If so, you may want to have a look at virt-manager. This makes the setup process so much easier. You can assign networks of various types to your VMs either at time of creation or add/delete/modify at any time afterwards.

If no GUI, then the CLI components can be installed separately:```
sudo apt install virt-install virt-clone virt-xml virt-bootstrap
```These are all explained in their man pages.

---

### Post by jusp on 2023-03-09
Thanks for the hint. Normally this would make very much sense, but in this case I am not particularly interested in a transparent setup for running qemu, but rather in finding out how quemu clients connect to the physical network :)

---

### Post by papakanush2 on 2023-03-09
Sounds familiar. In my experience, [FONT=monospace]restarting the default default network did the trick.[/FONT]

 ```
[FONT=monospace]$ sudo virsh net-start default[/FONT]
```

---

