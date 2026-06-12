---
title: "How to set static IP on VM"
date: 2016-05-04
forum: Virtualisation
---

### Post by satimis on 2016-05-04
Hi

host	ubuntu 14.04 desktop
vm	ubuntu 16.04 desktop

bridge-utils already installed on both host and vm

vm
Network	
Bridged Adapter
br0

On vm
ifconfig```

...
enp0s3    Link encap:Ethernet  HWaddr 08:00:27:42:e8:1f 
...

```
eth0 is NOT shown

Unable to connect Internet
NAT works without problem

Please advise how to fix the problem?  Thanks

[Edit]
On vm 

$ cat /etc/netwok/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.x.x
        dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx
        network         192.168.x.x
        netmask         255.255.255.0
        broadcast       192.168.x.255
        gateway         192.168.x.x
        bridge_ports    eth0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

Regards
satimis

---

### Post by KillerKelvUK on 2016-05-04
Hi satimis, so from what you have shown your guest (vm) has a network adapter named enp0s3...the naming here is driven by the udev rules and for whatever reason Ubuntu switched from using eth0, eth1 to what you are seeing.  As such you need to adopt the new naming convention or alter the config of the udev rules to create the device using your expected naming convention.

Second observation is that your /etc/network/interface script is incorrect if this is again for the guest (vm).  Your network bridge needs to be create on the _**host only**_, each guest then has an virtual interface connected to the network bridge on the host...this does not require any special config on your guest (vm).  I'd recommend you remove the linux-bridge package from the guest and alter its /etc/network/interface script to be as follows for a quick test...

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


# Your guest only needs 1 interface which is named enp0s3 as per your ifconfig output
auto enp0s3
iface enp0s3 inet dhcp

```

If you have configured the linux-bridge properly on the host and you have a functioning DHCP server in your subnet the above should dynamically allocate an IP to your guest (vm).  From this you can then alter the IP address to static and apply whatever values you require.  If this doesn't work or you don't have the configuration correct on the host please post back the results of ifconfig and the contents of the /etc/network/interface script from the host itself so we can take a closer look.

---

### Post by MAFoElffen on 2016-05-04
Wiat... am out the door... and will get back to this... You have the configs confused between the VM Host and VM guest... You said on Vm Guest: then had a the bro defined, which is a host config. Finals, work, then back home. (Tonight.)

---

### Post by satimis on 2016-05-04
Hi KillerKelvUK

Thanks for your advice.

It is very strange to me the settings on /etc/network/interfaces work for all VMs running Ubuntu 14.04/Linux Mint/Debian but not Ubuntu 16.04

Neither I could find /etc/udev/rules.d/70-persistent-net.rules file

&#10219; ls /etc/udev/```

hwdb.d  rules.d  udev.conf

```

&#10219; cat /etc/udev/udev.conf ```

# see udev.conf(5) for details
#
# udevd is started in the initramfs, so when this file is modified the
# initramfs should be rebuilt.

#udev_log="info"

```

&#10219; ls /etc/udev/rules.d/```

60-vboxadd.rules

```

&#10219; cat /etc/udev/rules.d/60-vboxadd.rules ```

KERNEL=="vboxguest", NAME="vboxguest", OWNER="vboxadd", MODE="0660"
KERNEL=="vboxuser", NAME="vboxuser", OWNER="vboxadd", MODE="0666"

```

&#10219; ls /etc/udev/hwdb.d/
No output

On Ubuntu 16.04 VM /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.x.x
        dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx
        network         192.168.x.x
        netmask         255.255.255.0
        broadcast       192.168.x.255
        gateway         192.168.x.x
        bridge_ports    eth0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```
I tried changing eth0 to enp0s3

It still didn't work

Host
&#10219; cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         xxx.xxx.xxx.xxx
        dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
        network         192.168.xx.xx
        netmask         255.255.255.0
        broadcast       192.168.xx.255
        gateway         192.168.xx.1
        bridge_ports    eth0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```
same as all VMs except "address"

Performed following steps on Ubuntu 16.04 VM

1.  $ sudo apt-get remove bridge-utils
2.  edit /etc/network/interfaces as;```

auto lo
iface lo inet loopback

auto enp0s3
iface enp0s3 inet dhcp

```

reboot Ubuntu 16.04 VM

&#10219; ifconfig```

enp0s3    Link encap:Ethernet  HWaddr 08:00:27:42:e8:1f  
          inet addr:192.168.8.2  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe42:e81f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2450 (2.4 KB)  TX bytes:6303 (6.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:338 (338.0 B)  TX bytes:338 (338.0 B)

```

Regards
satimis

---

### Post by KillerKelvUK on 2016-05-04
Hi satimis, this looks like you have got it working now, is that correct?

Here's some details behind the change of network adapter naming... [http://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes](http://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes)

---

### Post by satimis on 2016-05-04
> **KillerKelvUK said:**
> Hi satimis, this looks like you have got it working now, is that correct?
Hi KillerKelvUK,

Yes it worked able to connect Internet

> 
Here's some details behind the change of network adapter naming... [http://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes](http://askubuntu.com/questions/689070/network-interface-name-changes-after-update-to-15-10-udev-changes)

Performed following steps

&#10219; ip link```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 08:00:27:xx:xx:xx brd ff:ff:ff:ff:ff:ff

```

&#10219; sudo nano /etc/udev/rules.d/10-network.rules```

SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="08:00:27:xx:xx:xx", KERNEL=="enp0s3", NAME="eth0"

```

Reinstall bridge-utils and edit /etc/network/interfaces

&#10219; cat /etc/network/interfaces```

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.xx.xx
        dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
        network         192.168.xx.0
        netmask         255.255.255.0
        broadcast       192.168.xx.255
        gateway         192.168.xx.1
        bridge_ports    eth0

```

Reboot VM.

Still fail unable to connect Internet

&#10219; ifconfig```

&#10219; ifconfig
br0       Link encap:Ethernet  HWaddr 08:00:27:xx:xx:xx  
          inet addr:192.168.xx.xx  Bcast:192.168.xx.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe42:e81f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:532 (532.0 B)  TX bytes:6356 (6.3 KB)

eth0      Link encap:Ethernet  HWaddr 08:00:27:xx:xx:xx  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:772 (772.0 B)  TX bytes:7454 (7.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:8696 (8.6 KB)  TX bytes:8696 (8.6 KB)


```


[EDIT]
Host can ping VM IP
VM can ping Host IP
VM ping yahoo.com failed
VM ping 206.190.36.45 (yahoo IP) works


satimis

---

### Post by MAFoElffen on 2016-05-04
> **satimis said:**
> bridge-utils already installed on both host and vm

Uninstall bridge-utils from VM. Should only be installed on the host.

> **satimis said:**
> bridge-utils already installed on both host and vm
On vm
ifconfig```

...
enp0s3    Link encap:Ethernet  HWaddr 08:00:27:42:e8:1f 
...

```
eth0 is NOT shown

As described above, yes, you have port name enps3 in your vm...
> **satimis said:**
> bridge-utils already installed on both host and vm
On vm 
```

$ cat /etc/netwok/interfaces[code]
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.x.x
        dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx
        network         192.168.x.x
        netmask         255.255.255.0
        broadcast       192.168.x.255
        gateway         192.168.x.x
        bridge_ports    eth0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

That is incorrect for a VM interfaces file <> that would almost okay for a host file, so let me explain the host's interface file first

The host's interface file will contain the define for the bridge. Lets say you have 2 network ports on the host (names found via ifconfig) and say that the names were found to be eth0 and eth1...
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address         192.168.0.10
        dns-nameservers 8.8.8.8 8.8.8.4
        network         192.168.0.0
        netmask         255.255.255.0
        broadcast       192.168.0.255
        gateway         192.168.0.1

# The secondary network interface
auto eth1
iface eth1 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.0.101
        dns-nameservers 8.8.8.8 8.8.8.4
        network         192.168.0.0
        netmask         255.255.255.0
        broadcast       192.168.0..255
        gateway         192.168.0.1
        bridge_ports    eth1
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```
That would put a static address for your host as 192.168.0.10/24 and your bridge address as 192.168.0.101/24. if you do an ifconfig, the port that would show up would only be local, eth0 and br0... eth1 gets remapped as br0. With me so far?

Now for your vm's interface file:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto enps3
iface enps3 inet static
        address         192.168.0.102
        dns-nameservers 8.8.8.8 8.8.8.4
        network         192.168.0.0
        netmask         255.255.255.0
        broadcast       192.168.0.255
        gateway         192.168.0.1

```
That would set your vm to 192.168.0.102/24 on your hosts network. The bridge is transparent from the VM's side ... meaning that if the VM is set to "br0" is it's profile settings, it already has the gate open from it's side. From there on, it's just another machine on your host network.

Any other questions? Is that enough information to get you started? Tell me how it goes.

---

### Post by satimis on 2016-05-04
Hi MAFoElffen,

Thanks for your advice.

Let me explain the situation here.

There is a router on the network and the IP is assigned by the router.  I have only ONE NIC on this PC and it has been running for several years without problem with Host /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.xx.xx
        dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
        network         192.168.xx.0
        netmask         255.255.255.0
        broadcast       192.168.xx.255
        gateway         192.168.xx.1
        bridge_ports    eth0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

bridge-utils are installed on both VMs and Host.  The /etc/network/interfaces for both Host and VMs are almost the same. 

I have 26 VMs running on this PC and they are working without problem for years up to now able to connect Internet.  But only this newly installed VM (ubuntu16.04) fails to work.  I have another VM with ubuntu14.04 desktop installed about 2 weeks, same settings on /etc/network/interfaces.  It can connect Internet without problem.

I found a strange thing happened here.  I Just started the PC and ubuntu16.04 VM. The VM network worked without problem.  Browses could connect Internet and on terminal ping yahoo.com worked also.  Restarted VM then browser unabled to connect Internet nor on terminal ping yahoo.com worked.

It is very strange too me.  I also tried reboot PC without result.

Regards
satimis

---

### Post by KillerKelvUK on 2016-05-04
Hey satimis, so as a side point there is no need to install the linux-bridge package into your guest vm's unless you intend to do nested virtualisation and want to run a vm within a vm and use a bridged network configuration.  Typically only the host requires a network bridge, the guest vm's then just need a normal network adapter.  However as you have pointed out, you have been running this way for some time now on all your vm's so why the new issue about getting out to the internet?!

From reading your latest post I'd suggest your problem relates to some confused settings for DNS, I'd suggest you leave the other configurations alone for now but please can you post back the contents of the /etc/resolv.conf file for both your host and your guest?  Also please can you confirm that your router is configured to issue a DNS server IP as part of the DHCP lease information or have you always had to manually set the DNS/dns-nameserver IP's?

Last question, is the new Ubuntu 16.04 vm from a server image or a desktop image?

---

### Post by satimis on 2016-05-04
> **KillerKelvUK said:**
> Hey satimis, so as a side point there is no need to install the linux-bridge package into your guest vm's unless you intend to do nested virtualisation and want to run a vm within a vm and use a bridged network configuration.  Typically only the host requires a network bridge, the guest vm's then just need a normal network adapter.  However as you have pointed out, you have been running this way for some time now on all your vm's so why the new issue about getting out to the internet?!

For other running VMs if without bridge-utils installed network fails to work.  I can't understand why there is an issue on Ubuntu16.04

> 
From reading your latest post I'd suggest your problem relates to some confused settings for DNS, I'd suggest you leave the other configurations alone for now but please can you post back the contents of the /etc/resolv.conf file for both your host and your guest?  Also please can you confirm that your router is configured to issue a DNS server IP as part of the DHCP lease information or have you always had to manually set the DNS/dns-nameserver IP's?

I don't need to touch the router on installing a new VM.

The problem is here:-

ubuntu16.04
&#10219;  cat /etc.resolv.conf
it is an empty file

Host
&#10219;  cat /etc.resolv.conf```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

```

Other running VMs
&#10219;  cat /etc.resolv.conf```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

```

Added nameservers to ubuntu16.04 /etc/resolv.conf.  Then browser can browse Internet

Rebooted ubuntu16.04.  /etc/resolv.conf became an empty file again.  Browser failed to connect Internet.

Ubuntu16.04
ls -l /etc/resolv.conf```
 
lrwxrwxrwx 1 root root 29 May  4 11:01 /etc/resolv.conf -> ../run/resolvconf/resolv.conf

```

&#10219; ls -l /run/resolvconf/resolv.conf```
 
-rw-r--r-- 1 root root 202 May  5 07:52 /run/resolvconf/resolv.conf

```

After reboot the content of /etc/resolv.conf will be deleted.

> 
Last question, is the new Ubuntu 16.04 vm from a server image or a desktop image?
Desktop image

Thanks

satimis

[EDIT-1]
To stop /etc/resolv.conf rewritten on reboot, performed follows;

&#10219;sudo chattr +i /etc/resolv.conf ```

chattr: Operation not supported while reading flags on /etc/resolv.con.

```

&#10219; sudo chattr + /etc/resolv.conf ```

chattr: Operation not supported while reading flags on /etc/resolv.conf

```

Very strange it doesn't work on ubuntu16.04?  It worked on ubuntu14.04 previously.

[EDIT-2]
Problem solved by reallocating following line;
dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx

&#10219; cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx

# The primary network interface
auto eth0
iface eth0 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.xx.xx
#       dns-nameservers 2xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
        network         192.168.xx.0
        netmask         255.255.255.0
        broadcast       192.168.xx.255
        gateway         192.168.xx.1
        bridge_ports    eth0
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

/etc/resolv.conf won't be rewritten on reboot

I tried 3 times including one shutdown/restart

---

### Post by houstonbofh on 2016-05-05
You have a few problems going on at once here.

First is the "predictable network interface names" which is anything but...  Google for that and "sucks" and you will get a lot of hits! :)  You have fixed that by bringing back eth0, and that will work for now, but be ready for applications going forward to break with it. (Sigh)

You are installing bridge utils on your guests and you do not need to.  I have many KVM servers running, and none have bridge utils on the guests.  There is simply no way that can change routing on the host.  Here is an example of my interfaces file on a 16.04 server I am testing now.
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
It has a software firewall running to connect br1 to WAN, and light up br0 as LAN, and br2 and br3 as other networks.  Note that DHCP on br2 and br3 pulls from the firewall that is not running at boot, so it takes a while to boot.  (Thanks systemd and the sped up boot times....)

---

### Post by satimis on 2016-05-05
Hi houstonbofh,

Thanks for your advice.

I'm running Oracle VirtualBox here, sorry for not mentioning it on my original posting.

This PC has been working several years with about 28 VMs running.  If without bridge-utils installed on VM the network can't work.

I have built another 16.04 desktop VM.  The steps were same as the first 16.04 desktop.

ifconfig```

enp0s3    Link encap:Ethernet  HWaddr 08:00:27:xx:xx:xx
....

```

In the past I ran KVM at the beginning then changed to VirtualBox until now.  I may come back to KVM later after testing IAM

Regards
satimis

---

