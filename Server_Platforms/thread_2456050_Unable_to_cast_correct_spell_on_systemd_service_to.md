---
title: "Unable to cast correct spell on systemd service to make it wait"
date: 2021-01-03
forum: Server Platforms
---

### Post by adam-hardy on 2021-01-03
My gateway server serves the internet to my soho lan & wifi but I'm incapable of getting the services to start up correctly at boot and need to do it manually. 

There's the network that needs to come up first with the interfaces via **[FONT=courier new]netplan[/FONT]**

```
adam@gondolin:~$ cat /etc/netplan/01-netcfg.yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp5s0:
      dhcp4: yes
      dhcp6: yes
    eno1:
      dhcp4: no
      dhcp6: no
    wlp6s0:
      dhcp4: no
      dhcp6: no
  bridges:
    br0:
      interfaces:
        - eno1
        - wlp6s0
      addresses:
        - 192.168.0.3/24
      nameservers:
        addresses: [208.67.220.220,208.67.222.222]
adam@gondolin:~$ 

```

I make a bridge interface from the LAN [FONT=courier new]**eno1 **[/FONT]and wii[FONT=courier new]** wlp6s0**[/FONT]

I feed **[FONT=courier new]enp5s0[/FONT]** into [FONT=courier new]**ppp**[/FONT] and it creates the interface **[FONT=courier new]ppp0[/FONT]**

I then run **[FONT=courier new]iptables[/FONT]** with **[FONT=courier new]ppp0[/FONT]** as the external interface and **[FONT=courier new]br0[/FONT]** as the internal interface.

```
adam@gondolin:~$ sudo ifconfig 
[sudo] password for adam: 
br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.3  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::96b8:6dff:fe3d:4875  prefixlen 64  scopeid 0x20<link>
        ether 94:b8:6d:3d:48:75  txqueuelen 1000  (Ethernet)
        RX packets 1654286  bytes 839183556 (839.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1993283  bytes 2080059910 (2.0 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether e0:d5:5e:ad:b0:29  txqueuelen 1000  (Ethernet)
        RX packets 13063  bytes 2728893 (2.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 15487  bytes 2508727 (2.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xf7300000-f7320000  

enp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.11  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::e2d5:5eff:fead:b027  prefixlen 64  scopeid 0x20<link>
        ether e0:d5:5e:ad:b0:27  txqueuelen 1000  (Ethernet)
        RX packets 2662836  bytes 2787232223 (2.7 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2139332  bytes 922627747 (922.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xf7200000-f721ffff  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 37034  bytes 74412222 (74.4 MB)adam@gondolin:~$ sudo ifconfig 
[sudo] password for adam: 
br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.3  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::96b8:6dff:fe3d:4875  prefixlen 64  scopeid 0x20<link>
        ether 94:b8:6d:3d:48:75  txqueuelen 1000  (Ethernet)
        RX packets 1654286  bytes 839183556 (839.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1993283  bytes 2080059910 (2.0 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether e0:d5:5e:ad:b0:29  txqueuelen 1000  (Ethernet)
        RX packets 13063  bytes 2728893 (2.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 15487  bytes 2508727 (2.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xf7300000-f7320000  

enp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.11  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::e2d5:5eff:fead:b027  prefixlen 64  scopeid 0x20<link>
        ether e0:d5:5e:ad:b0:27  txqueuelen 1000  (Ethernet)
        RX packets 2662836  bytes 2787232223 (2.7 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2139332  bytes 922627747 (922.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xf7200000-f721ffff  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 37034  bytes 74412222 (74.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 37034  bytes 74412222 (74.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ppp0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1472
        inet 81.152.141.1  netmask 255.255.255.255  destination 172.16.11.38
        ppp  txqueuelen 3  (Point-to-Point Protocol)
        RX packets 2649359  bytes 2727516846 (2.7 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2131773  bytes 875459769 (875.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp6s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 94:b8:6d:3d:48:75  txqueuelen 1000  (Ethernet)
        RX packets 1682011  bytes 862225749 (862.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1987045  bytes 2132120902 (2.1 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 37034  bytes 74412222 (74.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ppp0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1472
        inet 11.22.33.44  netmask 255.255.255.255  destination 55.66.77.88 (both not the actual public IP addresses)
        ppp  txqueuelen 3  (Point-to-Point Protocol)
        RX packets 2649359  bytes 2727516846 (2.7 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2131773  bytes 875459769 (875.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp6s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether 94:b8:6d:3d:48:75  txqueuelen 1000  (Ethernet)
        RX packets 1682011  bytes 862225749 (862.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1987045  bytes 2132120902 (2.1 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```



When I launch the services one by one on the command line, everything is fine. In fact the network interfaces with [FONT=courier new]**netplan**[/FONT] are fine and booting goes smoothly - the problems are caused by **[FONT=courier new]ppp[/FONT]** and **[FONT=courier new]iptables[/FONT]**. I need to work out how to make systemctl wait for the interfaces before launching them.

This is the ppp service:

```
adam@gondolin:~$ sudo cat /etc/systemd/system/ppp.service
[Unit]
Description=PPPoE
Requires=network-online.target

[Service]
Type=forking
ExecStart=/usr/bin/pon provider
ExecStop=/usr/bin/poff -a

```

and this is the [FONT=courier new]**iptables**[/FONT], which needs to wait until [FONT=courier new]**ppp**[/FONT] has created the [FONT=courier new]**ppp0**[/FONT] interface:

```

adam@gondolin:~$ sudo cat /etc/systemd/system/iptables.service
[Unit]
Description=iptables
StartLimitBurst=5
StartLimitIntervalSec=0
BindsTo=sys-devices-virtual-net-ppp0.device
After=sys-devices-virtual-net-ppp0.device

[Service]
ExecStart=/etc/iptables/iptables start
ExecStop=/etc/iptables/iptables stop
Type=oneshot
RemainAfterExit=true
StandardOutput=journal

[Install]
WantedBy=multi-user.target

```

There are different results for this depending on whether I cold-boot or restart. Actually on checking the results again, it seems to function despite the foobar'd status message.  

```

adam@gondolin:~$ sudo systemctl status iptables
&#9679; iptables.service - iptables
     Loaded: loaded (/etc/systemd/system/iptables.service; enabled; vendor preset: enabled)
     Active: active (exited) since Sun 2021-01-03 00:36:07 GMT; 16h ago
    Process: 1294 ExecStart=/etc/iptables/iptables start (code=exited, status=0/SUCCESS)
   Main PID: 1294 (code=exited, status=0/SUCCESS)

Jan 03 00:36:07 gondolin iptables[1295]: log ()
Jan 03 00:36:07 gondolin iptables[1295]: {
Jan 03 00:36:07 gondolin iptables[1295]:     test -x "$LOGGER" && $LOGGER -p info "$1"
Jan 03 00:36:07 gondolin iptables[1295]: }
Jan 03 00:36:07 gondolin iptables[1331]: iptables v1.8.4 (legacy): host/network `EXT_IP' not found
Jan 03 00:36:07 gondolin iptables[1331]: Try `iptables -h' or 'iptables --help' for more information.
Jan 03 00:36:07 gondolin iptables[1333]: iptables v1.8.4 (legacy): host/network `EXT_IP' not found
Jan 03 00:36:07 gondolin iptables[1333]: Try `iptables -h' or 'iptables --help' for more information.
Jan 03 00:36:07 gondolin iptables[1294]: Finished executing iptables firewall /etc/iptables/iptables.fw
Jan 03 00:36:07 gondolin systemd[1]: Finished iptables.

```

It seems that the trick with 

[FONT=courier new][B] BindsTo=sys-devices-virtual-net-ppp0.device
[/B][/FONT]
doesn't really work, or at least not reliably. Sometimes it makes it, sometimes it doesn't.

So somehow I need to make **[FONT=courier new]iptables[/FONT]** wait longer.

---

### Post by TheFu on 2021-01-03
[https://fedoramagazine.org/systemd-unit-dependencies-and-order/](https://fedoramagazine.org/systemd-unit-dependencies-and-order/) has some tips that might not be intuitively obvious. That link is part of a series that I need to review, since it seems nobody has come to their senses and dumped systemd from the most-used distros. Sigh.
v
Something else you might consider is splitting the large netplan, into separate files for each connection, in the /etc/netplan/ directory? I don't know if this actually works that way.

Or you could just skip netplan and create a script that gets run using the same commands you manually run, in the correct order, using a systemd unit file as the controller.

---

### Post by adam-hardy on 2021-01-04
The problem with the simple [FONT=courier new]**after**[/FONT] and [FONT=courier new]**before**[/FONT] statements in the service definitions is that the system doesn't recognise that the launched processes haven't finished initialising before it thinks everything's fine and goes onto the next service.

So it kicks off [FONT=courier new]**ppp.service**[/FONT] and presumably the script returns but the initialisation isn't finished. That means that the system then kicks off [FONT=courier new]**iptables.service**[/FONT], but before [FONT=courier new]**ppp**[/FONT] has created the new interface.

---

### Post by adam-hardy on 2021-02-17
Would a quick and dirty solution work, like making my **iptables.service** the last service that **systemd** loads? Is there a way to do that?

---

### Post by kevdog on 2021-02-19
You could create a systemd timer file that calls your systemd service file like 1 min after boot. The example is down the list of responses a ways.

[https://stackoverflow.com/questions/43001223/how-to-ensure-that-there-is-a-delay-before-a-service-is-started-in-systemd/44737570](https://stackoverflow.com/questions/43001223/how-to-ensure-that-there-is-a-delay-before-a-service-is-started-in-systemd/44737570)

---

### Post by SeijiSensei on 2021-02-19
As I recall, iptables rules can be written to the kernel before the relevant devices are created.  On older RedHat machines, the iptables script would be run before the network was started to avoid giving remote attackers an opportunity. Bringing up the network before the iptables rules creates a momentary vulnerability.

---

