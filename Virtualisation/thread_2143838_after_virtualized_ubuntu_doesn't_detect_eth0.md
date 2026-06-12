---
title: "after virtualized ubuntu doesn't detect eth0"
date: 2013-05-10
forum: Virtualisation
---

### Post by argie01 on 2013-05-10
Hello,

I had an ubuntu 10.04.2 LTS, and I virtualized it using vmware converter software.
Everything was right, except because eth0 is not detect by ubuntu (but it was detect by vmware converter software at the moment of the virtualization conversion process).
So, I edit interfaces file and add the new config for eth0 manually, because the original physical computer was using dhcp, and the virtualized computer requires an static IP.

So, the configuration I wrote is this:

```

    auto eth0
    iface eth0 inet static
    address 192.168.1.102
    netmask 255.255.255.0
    broadcast 192.168.1.255
    network 192.168.1.0
    gateway 192.168.1.1
    dns-nameserver 192.168.1.25
    dns-search af.local

```

When I do a networking restart I got these messages:

```
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
```

I've read here a possible solution

[http://www.serenux.com/2009/11/howto-fix-a-missing-eth0-adapter-after-moving-ubuntu-server-from-one-box-to-another/](http://www.serenux.com/2009/11/howto-fix-a-missing-eth0-adapter-after-moving-ubuntu-server-from-one-box-to-another/)

but it didn't work in my case.

Thank you for your help.

---

### Post by heiko_s on 2013-05-12
I'm not familiar with VMware, but my guess is that VMware uses a virtual bridge like Xen does. In that case you don't define eth0, as it gets only used by the bridge. I know how to configure a bridge under Xen, but I suggest you search for virtual bridge configuration under VMware.

Here the reasoning:
On a bare-metal installation, Ubuntu would use the physical eth0 NIC to connect to the network.
A hypervisor like Xen or VMware that can run multiple VMs cannot allow a VM to use the physical eth0 directly. So it sets up a virtual network bridge and lets the VMs connect to that bridge. The VM connects to the virtual bridge using a virtual network interface.

Hope it points you in the right direction.

---

### Post by argie01 on 2013-05-13
Thank you for your answer, but in my experience Vmware works differently as you think. According to what I read on several webs on internet there shouldn't be any problem with eth0 after a P2V conversion...
Of course, I have a problem :), but if you read the link I wrote that should be the solution... but it isn't in my case... :(

Regards.

---

### Post by heiko_s on 2013-05-13
Maybe [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1032790]("http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1032790") or [http://conshell.net/wiki/index.php/Linux_P2V]("http://conshell.net/wiki/index.php/Linux_P2V") - see "When things go wrong" - or [http://stackoverflow.com/questions/175876/how-do-i-fix-my-vms-network-connection-if-it-seems-to-be-running-ok-from-the-ho]("http://stackoverflow.com/questions/175876/how-do-i-fix-my-vms-network-connection-if-it-seems-to-be-running-ok-from-the-ho")?

This [http://www.vmware.com/support/ws55/doc/ws_net.html]("http://www.vmware.com/support/ws55/doc/ws_net.html") gives an overview of the network options available with VMware Workstation 5.5. Of course VMware also supports bridged networks, so it may be best to have a look at the VMware network configuration.

By the way, there are so many possible options and you haven't been very specific. Here some questions:

1. What VMware are you using? VMware Workstation, ESXi, etc.?
2. What is your host operating system?
3. What is your VM OS? (You specified Ubuntu 10.04 LTS, but is it the server edition? The link you posted refers specifically to the server edition.)

> So, I edit interfaces file and add the new config for eth0 manually, because the original physical computer was using dhcp, and the virtualized computer requires an static IP.

Why does the new virtualized computer require a static IP? As I pointed out before, if you choose bridged networking, you can continue using a DHCP server (e.g. on your router) to provide an IP to the VM, as the network will be a simple layer 2 network.

I suggest to run ifconfig in your host OS (I hope its Linux, but I think ipconfig under Windows may work) to see if a bridge is there. If yes, edit the interfaces file in your Ubuntu guest, comment out the eth0 static IP configuration and add:
```
auto eth2
iface eth0 inet dhcp
```
to enable DHCP. Of course your DHCP server must be enabled.

---

### Post by argie01 on 2013-05-13
Thank you for your answer.
I was reading this post: [http://stateless.geek.nz/2007/02/01/ubuntu-and-vmware-losing-your-ethernet-device-when-migrating/](http://stateless.geek.nz/2007/02/01/ubuntu-and-vmware-losing-your-ethernet-device-when-migrating/)
And what I did to fixed this problem was delete all the content inside the file /etc/udev/rules.d/70_persistent-net.rules. Then I rebooted, edited "interfaces" and changed eth0 for eth3. I did it because when I run ifconfig there was an eth3 interface detected by ubuntu.
After a "networking restart" everything is fine.

Regards.

---

### Post by heiko_s on 2013-05-13
Great!

---

