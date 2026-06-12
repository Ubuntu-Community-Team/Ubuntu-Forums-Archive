---
title: "Gutsy Xen Windows HVM networking problem"
date: 2008-01-10
forum: Virtualisation
---

### Post by biswajit on 2008-01-10
Hi,


I've been able to install and run Windows XP SP2 on my Intel Core2 CPU with VT support in Gutsy amd64 with the following configuration file:

name = 'dba-winvm'
kernel = '/usr/lib/xen-ioemu-3.1/boot/hvmloader'
builder = 'hvm'
device_model = '/usr/lib/xen-ioemu-3.1/bin/qemu-dm'
memory = 768
shadow_memory = 8
#vif = ['ip=192.168.1.69,mac=aa:bb:00:00:00:01,type=ioemu, bridge=xenbr0']
vif = ['mac=00:16:3e:11:12:22,type=ioemu, bridge=xenbr0']
#vif = ['type=ioemu, bridge=xenbr0']
disk = ['file:/home/xen/domains/dba-winvm/dba-winvm-disk.img,hda,w', 'file:/home/shared/downloads/winxpsp2.iso,hdc:cdrom,r']
boot = 'cd'
soundhw='sb16'
localtime=1
vcpus=2
usb=1
usbdevice='tablet'
vnc=1
vncconsole=1

However, I just cannot get networking going in the Windows vm. Windows does not acquire an IP from our DHCP server, instead gives itself a 169.254.155.105 auto IP address, and the icon in the system tray indicates that the network is disconnected. 

As you can see from the config file, I've tried setting a static address as well as specifying mac address, but to no avail.

In /etc/xen/xend-config.sxp, I have uncommented:
(network-script network-bridge)
(vif-script vif-bridge)

and commented out
#(network-script network-dummy) - this doesn't seem to make any difference




#brctl show
bridge name     bridge id               STP enabled     interfaces
xenbr0             8000.00ff89c9e339       no              tap0
                                                           vif8.0


# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:D1:6A:2E:B9  
          inet addr:192.168.1.126  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe6a:2eb9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:11919249 (11.3 MB)  TX bytes:1153881 (1.1 MB)
          Base address:0xecc0 Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:185985653 (177.3 MB)  TX bytes:185985653 (177.3 MB)

tap0      Link encap:Ethernet  HWaddr 00:FF:89:C9:E3:39  
          inet6 addr: fe80::2ff:89ff:fec9:e339/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1878 (1.8 KB)  TX bytes:468 (468.0 b)

vif8.0    Link encap:Ethernet  HWaddr FE:FF:FF:FF:FF:FF  
          inet6 addr: fe80::fcff:ffff:feff:ffff/64 Scope:Link
          UP BROADCAST RUNNING NOARP  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:13 overruns:0 carrier:0
          collisions:0 txqueuelen:32 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

xenbr0    Link encap:Ethernet  HWaddr 00:FF:89:C9:E3:39  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:393 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57894 (56.5 KB)  TX bytes:90 (90.0 b)



Extract from /var/log/xen/xend.log:

[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: VBD.set_device not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: VBD.set_mode not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: VBD.set_type not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: VM.get_auto_power_on not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: VM.set_auto_power_on not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: VM.set_VCPUs_max not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: VM.set_VCPUs_at_startup not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: debug.get_all not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: console.get_other_config not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: console.set_other_config not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: VIF.get_network not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: VIF.set_device not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: VIF.set_MAC not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: VIF.set_MTU not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: session.get_all_records not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: event.get_record not found
[2008-01-10 15:55:45 10759] WARNING (__init__:1094) API call: event.get_all not found



Does anyone know of a solution? Would really appreciate any information.

Thanks.

---

### Post by Astaroth_PoD on 2008-02-05
I have the exact same problem - and I've tried everything I can think of.

Also, Xen on Gutsy seems extremely unstable - booting a domU works, network doesn't, rebooting it hangs the whole dom0, in addition to random dom0 lockups if I fiddle around too much.

Anyone have a Windows domU working in Gutsy?

---

### Post by sudoyang on 2008-02-05
This works fine for me.  I jotted some notes down on my blog: 

[http://fong.homelinux.com/wordpress/?p=24]("http://fong.homelinux.com/wordpress/?p=24")

Note that I'm using the Server edition of Ubuntu 7.10, but it should be the same.

---

