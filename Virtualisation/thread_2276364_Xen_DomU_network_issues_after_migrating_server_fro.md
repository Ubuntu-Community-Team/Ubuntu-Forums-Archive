---
title: "Xen: DomU network issues after migrating server from debian to ubuntu"
date: 2015-05-02
forum: Virtualisation
---

### Post by Mona on 2015-05-02
I am trying to migrate our xen server from debian wheezy to Ubuntu 14.04 LTS server. On Debian everything works fine: 4 linux DomUs and 1 windows HVM DomU are up and running. I then installed Ubuntu 14.04. LTS with xen-hypervisor-4.4-amd64. The linux domUs are doing fine on the new server. The windows hvm guest starts, but has no network, and I just don't get why. To be honest, I don't even know where to look for the mistake I obviously made. Can someone give me hint? 

/etc/network/interfaces
```

auto eth0 xenbr0

iface xenbr0 inet dhcp
  bridge_ports eth0

iface eth0 inet manual
```

/etc/xen/xend-config.sxp
```
(network-script network-bridge)
(vif-script vif-bridge)
(dom0-min-mem 1024)
(enable-dom0-ballooning no)
(total_available_memory 0)
(dom0-cpus 0)
(vnc-listen '0.0.0.0')
(vncpasswd 'secret')
(keymap 'de')

```

/etc/xen/win.cfg
```
builder = "hvm"
name = "win"
memory = "8192"
vcpus = 4
vif = ['mac=00:16:3E:43:38:E2, bridge=xenbr0']
disk =  [
        'phy:/dev/mapper/pegasus-sol_hdd1,hda,w',
        'phy:/dev/mapper/pegasus-sol_hdd2,hdb,w'
        ]
vnc = 1
vnclisten = "0.0.0.0"
usbdevice = 'tablet'
boot="cd"
keymap='de'
```

# sudo brctl show (before domU starts):
```

bridge name     bridge id               STP enabled     interfaces
xenbr0          8000.00252242b475       no              eth0
                                                        vif11.0
                                                        vif5.0
                                                        vif8.0

```

# sudo brctl show (after  domU has been started):
```
bridge name     bridge id               STP enabled     interfaces
xenbr0          8000.00252242b475       no              eth0
                                                        vif11.0
                                                        vif13.0
                                                        vif13.0-emu
                                                        vif5.0
                                                        vif8.0

```

# sudo xl network-list win
```
Idx BE Mac Addr.         handle state evt-ch   tx-/rx-ring-ref BE-path
0   0  00:16:3e:43:38:e2     0     1     -1    -1/-1          /local/domain/0/backend/vif/13/0
```

the domU comes up, I see the login screen on vnc. After the login the screen shows "preparing desktop..." for a decade and nothing happens.

there  is no network activity at all:

# sudo tcpdump -n -i xenbr0 ether src 00:16:3e:43:38:e2
```
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on xenbr0, link-type EN10MB (Ethernet), capture size 65535 bytes
[10 minutes nothing]
^C
0 packets captured
0 packets received by filter
0 packets dropped by kernel
```

the domU is not crashed. It responds to "xl commands" (e. g. xl shutdown win) but is unreachable via the network.

---

