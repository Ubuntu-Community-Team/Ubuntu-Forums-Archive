---
title: "QEMU/KVM Basic NAT"
date: 2017-01-13
forum: Virtualisation
---

### Post by &amp;*@Fth&amp;% on 2017-01-13
I have *very* little knowledge of networking, so please pardon any ignorance or incorrect terms.
I need to set up NAT for my Windows VM, but for some reason any network I set up using virt-manager's virtual network wizard simply doesn't work.

I saw on the mega-thread that NAT should work out-of-the-box, but without any manually added virtual networks, the only options the menu gives me are macvtap. I have no idea what that is, but it only allows bridge, VEPA, private, or passthrough modes, and I don't think any of those are what I want.

From what I can see in the manual, the only way I can create a network using virsh requires an XML, which I don't know how to make.

---

### Post by Doug S on 2017-01-14
You want to use a bridge.
If you want to use virsh, then it would be virsh edit, which in turn would edit he VM definition .xml file.

---

### Post by KillerKelvUK on 2017-01-14
How is your networking currently set up in virt-manager...can you find your page like the below and send back a screen shot?

[IMG]https://s29.postimg.org/o2jztdspz/QEMU_Networking.png[/IMG]

---

### Post by &amp;*@Fth&amp;% on 2017-01-14
I want the VM to be connected to whatever network the host is connected to. If I, for example, connect to a different WiFi network on the host, the guest will see it as unplugging one ethernet cable and plugging in a different one.

If that's what bridging does, then great. But I've read that bridging only works on wired networks, which isn't great.

[IMG]https://s23.postimg.org/fife5zwi3/Screenshot_20170114_082642.png[/IMG]

---

### Post by KillerKelvUK on 2017-01-14
The core difference between a guest that is using NAT as its network access vs. routing via bridge is whether you want to be able to remotely access services running from your guest.  To be clearer...say you wanted to run a website from your Windows VM and like any website you want it to be available from your local network or maybe also the internet then in this use case you would need to configure a network bridge or similar.  If however you just want your Windows guest to be able to access the internet and browse or connect to an online game server then NAT is fine for this and simpler to set up.

Can you post back here the XML for the guest when you added in the virtual network adapter when you tested NAT previously?

---

### Post by &amp;*@Fth&amp;% on 2017-01-14
All I need to do is browse the web and play multiplayer games with a decent ping.

My XML:
```

<domain type='kvm'>
  <name>Windows10-N-x64</name>
  <uuid>b588e2cb-b180-4584-b249-ff6c84408df6</uuid>
  <title>Windows 10 N 64-Bit</title>
  <memory unit='KiB'>8388608</memory>
  <currentMemory unit='KiB'>8388608</currentMemory>
  <vcpu placement='static'>4</vcpu>
  <os>
    <type arch='x86_64' machine='pc-i440fx-yakkety'>hvm</type>
    <loader readonly='yes' type='pflash'>/usr/share/OVMF/OVMF_CODE.fd</loader>
    <nvram>/var/lib/libvirt/qemu/nvram/Windows10-N-x64_VARS.fd</nvram>
  </os>
  <features>
    <acpi/>
    <apic/>
    <hyperv>
      <relaxed state='on'/>
      <vapic state='on'/>
      <spinlocks state='on' retries='8191'/>
    </hyperv>
  </features>
  <cpu mode='host-passthrough'>
    <topology sockets='1' cores='4' threads='1'/>
  </cpu>
  <clock offset='localtime'>
    <timer name='rtc' tickpolicy='catchup'/>
    <timer name='pit' tickpolicy='delay'/>
    <timer name='hpet' present='no'/>
    <timer name='hypervclock' present='yes'/>
  </clock>
  <on_poweroff>destroy</on_poweroff>
  <on_reboot>restart</on_reboot>
  <on_crash>restart</on_crash>
  <pm>
    <suspend-to-mem enabled='no'/>
    <suspend-to-disk enabled='no'/>
  </pm>
  <devices>
    <emulator>/usr/bin/kvm-spice</emulator>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' cache='writeback'/>
      <source file='/var/lib/libvirt/images/Windows10-N-x64.img'/>
      <target dev='vda' bus='virtio'/>
      <boot order='1'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x08' function='0x0'/>
    </disk>
    <disk type='file' device='disk'>
      <driver name='qemu' type='raw' cache='writeback'/>
      <source file='/var/lib/libvirt/images/Storage.img'/>
      <target dev='vdb' bus='virtio'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x04' function='0x0'/>
    </disk>
    <controller type='pci' index='0' model='pci-root'/>
    <controller type='usb' index='0' model='nec-xhci'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x05' function='0x0'/>
    </controller>
    <interface type='network'>
      <mac address='52:54:00:97:b7:8a'/>
      <source network='vmnet'/>
      <model type='rtl8139'/>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x03' function='0x0'/>
    </interface>
    <input type='mouse' bus='ps2'/>
    <input type='keyboard' bus='ps2'/>
    <sound model='ich9'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x06' function='0x0'/>
    </sound>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x0'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0a' function='0x0'/>
    </hostdev>
    <hostdev mode='subsystem' type='pci' managed='yes'>
      <source>
        <address domain='0x0000' bus='0x01' slot='0x00' function='0x1'/>
      </source>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x0b' function='0x0'/>
    </hostdev>
    <memballoon model='virtio'>
      <address type='pci' domain='0x0000' bus='0x00' slot='0x09' function='0x0'/>
    </memballoon>
  </devices>
</domain>

```

---

### Post by KillerKelvUK on 2017-01-14
So that config looks good, you could optimise and use the virtio drivers like on the other thread but Windows will work with the rtl8139 driver so why isn't this working for you, whats happens when you try to browse to google from inside the vm?

The only thing odd to me is the screenshot you added showing a 'domain' reference which I don't have, what's your host OS version and version of virt-manager you're using?

Are you still using Synergy, is that still working?

---

### Post by &amp;*@Fth&amp;% on 2017-01-14
Trying to access the internet from within the VM reports it has no internet connection, which is verified by ping and the network utility in the system tray.

I'm using Kubuntu 16.10 Yakkety, and the guest is, as the name implies, Windows 10 N Home, x86_86.

Synergy doesn't work anymore. It used to work, and outside internet didn't, but after messing with the network configuration it stopped. Adding a macvtap nic doesn't help either.
Setting the second nic to macvtap bridge on eno1 seems to get the internet working, but again, that wouldn't work if I was on WiFi.

---

### Post by KillerKelvUK on 2017-01-14
Erm didn't ask about the Windows guest, asked for version of virt-manager?

Please post back the results of ifconfig and the contents of /etc/network/interfaces.

macvtap would effectively allow you to passthrough an interface to your guest and configure it within the guest but you'd then loose that interface on your host.  

When you say messing with the network configuration was that on host or guest i.e. have you potentially broken the Windows guest network stack/config?

---

### Post by &amp;*@Fth&amp;% on 2017-01-14
Oh, duh. virt-manager is version 1.3.2.

ifconfig:
```

eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 40:8d:5c:bd:03:e4  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7f00000-f7f20000  

enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.28  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::812c:fad0:81c4:2aab  prefixlen 64  scopeid 0x20<link>
        ether 40:8d:5c:bd:03:e2  txqueuelen 1000  (Ethernet)
        RX packets 4902531  bytes 7148939130 (7.1 GB)
        RX errors 0  dropped 86  overruns 0  frame 0
        TX packets 2364383  bytes 167518490 (167.5 MB)
        TX errors 3  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 5588  bytes 548756 (548.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5588  bytes 548756 (548.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.0.1  netmask 255.255.255.0  broadcast 192.168.0.255
        ether 00:00:00:00:00:00  txqueuelen 1000  (Ethernet)
        RX packets 948  bytes 342727 (342.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 789  bytes 1134513 (1.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp4s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.29  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::b0e2:6ecf:d34c:ac8e  prefixlen 64  scopeid 0x20<link>
        ether 7c:5c:f8:91:83:8b  txqueuelen 1000  (Ethernet)
        RX packets 62524  bytes 4395055 (4.3 MB)
        RX errors 0  dropped 46  overruns 0  frame 0
        TX packets 3129  bytes 377122 (377.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

/etc/network/interfaces:
```

auto lo
iface lo inet loopback

```


I haven't changed anything on the guest's side, just adding and  removing NICs, reconfiguring them, and adding and removing virtual  networks. I doubt I've broken anything inside Windows.

---

### Post by KillerKelvUK on 2017-01-14
K so from ifconfig we can see...

[LIST]
[*]enp3s0: looks like a wired ethernet connection and it has an IP 192.168.1.28
[*]wlp4s0: looks like a wifi connection and it has an IP of 192.168.1.29
[*]virbr0: is your NAT device created by virt-manager and has an IP of 192.168.0.1
[/LIST]

So first question, you have 2 network interfaces on your host with an IP (enp3s0 and wlp4s0)...why, what are you trying to do with that?

Next please can you start the Windows guest and let it boot, then back on the host and post back another ifconfig output but also the contents of /etc/resolv.conf as well as the output of 'brctl show'.

---

### Post by &amp;*@Fth&amp;% on 2017-01-14
Oh. I didn't even realize. I have ethernet plugged in, but it auto-connected to the WiFi because it was in my known list or whatever it's called. So that's why the internet on the host didn't go out when I added the ethernet bridge. Turned that off now.
For this test, I removed the second bridge NIC from the guest, so it only has the NAT NIC.

ifconfig:
```

eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 40:8d:5c:bd:03:e4  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf7f00000-f7f20000  

enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.28  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::812c:fad0:81c4:2aab  prefixlen 64  scopeid 0x20<link>
        ether 40:8d:5c:bd:03:e2  txqueuelen 1000  (Ethernet)
        RX packets 5311950  bytes 7742799019 (7.7 GB)
        RX errors 0  dropped 86  overruns 0  frame 0
        TX packets 2556961  bytes 181736876 (181.7 MB)
        TX errors 3  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 6060  bytes 600918 (600.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6060  bytes 600918 (600.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.1  netmask 255.255.255.0  broadcast 192.168.0.255
        ether fe:54:00:97:b7:8a  txqueuelen 1000  (Ethernet)
        RX packets 2847  bytes 840751 (840.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2297  bytes 3719135 (3.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

vnet0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::fc54:ff:fe97:b78a  prefixlen 64  scopeid 0x20<link>
        ether fe:54:00:97:b7:8a  txqueuelen 1000  (Ethernet)
        RX packets 1765  bytes 509833 (509.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2417  bytes 2635534 (2.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp4s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 7c:5c:f8:91:83:8b  txqueuelen 1000  (Ethernet)
        RX packets 68098  bytes 4780602 (4.7 MB)
        RX errors 0  dropped 46  overruns 0  frame 0
        TX packets 3202  bytes 385466 (385.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```


/etc/resolv.conf:
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

```


brctl show:
```

bridge name    bridge id        STP enabled    interfaces
virbr0        8000.fe540097b78a    yes        vnet0

```

---

### Post by KillerKelvUK on 2017-01-15
Forgot to ask whether you know what the eno1 interface is on your host? (how many NIC ports are on your host?)

So the configuration and results you've put above say this should be working I believe.  So when your Windows guest is booted with the above conditions is it receiving an IP address, what are its credentials?  Can you share the details as per the below screen shot from my Windows guest.  Can you also share the output of a ping and traceroute to your local router?

[IMG]https://s28.postimg.org/45rjb7d9p/Windows_Network.jpg[/IMG]

---

### Post by &amp;*@Fth&amp;% on 2017-01-15
Huh... that's very odd. It wasn't working before, but now it is.
1. Just NAT NIC, no internet.
2. Added macvtap bridge NIC, got internet through that one and not the NAT NIC.
3. Removed the macvtap bridge, no internet, as seen in my last post.
4. Rebooted the host. Now the guest has internet.

I'm not complaining that it works now, but seriously, what the heck is going on here??

---

### Post by KillerKelvUK on 2017-01-16
If you've been using the network configuration tools in virt-manager then this changes the OS network services configurations...if you've done a lot of this and then some manual tinkering it could just have left some bad config active which the reboot cleared.

---

