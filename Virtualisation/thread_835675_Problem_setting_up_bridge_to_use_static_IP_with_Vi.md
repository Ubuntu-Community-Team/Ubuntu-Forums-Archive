---
title: "Problem setting up bridge to use static IP with VirtualBox"
date: 2008-06-20
forum: Virtualisation
---

### Post by tennis_mutt on 2008-06-20
Trouble with Static IP's with VirtualBox
I am setting up a system to test various platforms with. I am using Ubuntu 8.04 64 with VirtualBox 1.6.2 on a system with 1 network card. I want to use static ip addresses which is giving me a lot of problems. The setup I would like is as follows:
    Ubuntu host ip is 192.168.1.140
    Windows XP is 192.168.1.141
    Open Solaris is 192.168.1.142
    Red Hat Enterprise Linux is 192.168.1.143

I have installed all these guests using NAT and they all loaded and worked OK.

When I try to add the bridges to the interfaces file I run into problems even before I try to add then to the VirtualBox with VBoxAddIf. When the first bridge br0 is added it removes the static IP from the host which leaves the hosts network access failing. The first bridge also has the same MAC address as the host network card eth0, Is this correct.

**The "interfaces" file**

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.140
netmask 255.255.255.0
gateway 192.168.1.110

auto br0
iface br0 inet static
address 192.168.1.141
netmask 255.255.255.0
gateway 192.168.1.110
bridge_ports eth0

auto br1
iface br1 inet static
address 192.168.1.142
netmask 255.255.255.0
gateway 192.168.1.110
bridge_ports eth0

auto br2
iface br2 inet static
address 192.168.1.143
netmask 255.255.255.0
gateway 192.168.1.110
bridge_ports eth0
```


**The output of ifconfig**

```
br0 Link encap:Ethernet HWaddr 00:1b:b9:c6:d5:6b
inet addr:192.168.1.141 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::21b:b9ff:fec6:d56b/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:279 errors:0 dropped:0 overruns:0 frame:0
TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:51054 (49.8 KB) TX bytes:5653 (5.5 KB)

br1 Link encap:Ethernet HWaddr e2:94:4a:19:48:6d
inet addr:192.168.1.142 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::e094:4aff:fe19:486d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:3951 (3.8 KB)

br2 Link encap:Ethernet HWaddr 42:80:89:fd:46:89
inet addr:192.168.1.143 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::4080:89ff:fefd:4689/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:3951 (3.8 KB)

eth0 Link encap:Ethernet HWaddr 00:1b:b9:c6:d5:6b
inet6 addr: fe80::21b:b9ff:fec6:d56b/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:297 errors:0 dropped:0 overruns:0 frame:0
TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:59072 (57.6 KB) TX bytes:6195 (6.0 KB)
Interrupt:20 Base address:0xe800

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1766 errors:0 dropped:0 overruns:0 frame:0
TX packets:1766 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:88300 (86.2 KB) TX bytes:88300 (86.2 KB)

```

I have read just about everything I could find in these forums over the last 2 weeks and have come up with no solutions.

I am not showing all the VirtualBox info because the host network is not working at this point.

I do not think that the problem is with VirtualBox.  It is most likely with the way I am trying to create the bridges.  It seems that most documentation drops off at this point or is dealing with bridging seperate networks with multiple network cards

If anyone has something like this working I would like to see the "interfaces" file and the output of ifconfig to study.

I sure that I am doing something wrong but I am at a loss now.

I have tried this with vmware and it worked without any problem.

If I can see the ifconfig output of a working system with static IP address it may help, or if someone has a link to some good documentation.

---

### Post by kell_pt on 2008-07-06
This exactly what I'm trying to do... insofar I haven't managed to reach any solution. Anyone has any ideas on this?

---

### Post by tennis_mutt on 2008-07-07
I finally got this to work. Many of my solutions were found from some posts by **irving** and **karyonix** in a very long thread that was called **HOWTO VirtualBox Host networking**.  Below is a summary of the steps needed to get this to work.


* Download latest package from [www.virtualbox.org](www.virtualbox.org) for Ubuntu 8.04 amd64 (Hardy)
* Install package libqt3-mt
* Install package with sudo dpkg -i <pkg_name> or click on package icon
* Add user's who will use VirtualBox to vboxusers group
* sudo usermod -a -G vboxusers <username>
* log out and log back in to make new group active for you
* I added a user vboxuser to control the VirtualBox setup and added it to vboxusers group.  This is not required but I think it is better then using a regular user for vbox maintenance.


**Setting up bridge for static IP's**

The following commands will set up the bridge and tap devices to setup the network and bring it up for use.  Some of these settings will be temporary until the system is rebooted.  To make these changes hold after a reboot the /etc/network/interfaces file will have to be edited.

One of the problems that I had was that the eth0 device would not function after the br0 bridge was set up.  If appears that the br0 device replaces the eth0 device when the bridge is active, so setting to the main network interface will have to be made to the br0 device.

After everything is set up the interface name in virtualbox should be set to tap0, tap1 or tap2 for the different operating systems.  You must also set the Attached to: option to host interface.  The guest operating systems can then be set to the static ip and assign it in the guest os just as if it had it's own network card.

install packages bridge-utils and uml-utilities
type sudo modprobe tun to load tun module into memory.  Then add a line with the word tun to the end of the file /etc/modules.  This will force the load when the system is rebooted.  Now type the following lines to create tap interfaces for virtual network cards.

```
sudo tunctl -u vboxuser -t tap0
sudo ifconfig tap0 0.0.0.0 promisc up
sudo tunctl -u vboxuser -t tap1
sudo ifconfig tap1 0.0.0.0 promisc up
sudo tunctl -u vboxuser -t tap2
sudo ifconfig tap1 0.0.0.0 promisc up
sudo chmod 0666 /dev/net/tun
sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif br0 tap0
sudo brctl addif br0 tap1
sudo brctl addif br0 tap2
sudo ifconfig br0 192.168.1.140 netmask 255.255.255.0 broadcast 192.168.1.255 up
sudo ifconfig  eth0 0.0.0.0 promisc up
sudo route add default 192.168.1.110
```

**Interfaces file**

```
auto lo
iface lo inet loopback

iface eth0 inet manual

auto tap0 tap1 tap2
iface tap0 inet manual
   tunctl_user vboxuser
iface tap1 inet manual
   tunctl_user vboxuser
iface tap2 inet manual
   tunctl_user vboxuser

auto br0
iface br0 inet static
   bridge_ports eth0 tap0 tap1 tap2
   bridge_maxwait 0
   address 192.168.1.140
   netmask 255.255.255.0
   gateway 192.168.1.110
```


I am currently building a new clean system to make sure these steps are correct.  If I find anthing else I will post it here.

---

### Post by tennis_mutt on 2008-07-08
Found a few more things while doing a clean install.

**To get USB devices to work and not get any errors**

Edit file /etc/init.d/mountdevsubfs.sh
Remove comments from the following 4 lines

Change from:

#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

Change to:

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb



**To get /dev/net/tun permissions to be set correctly on reboot**

To make /dev/net/tun permissions changes stay after a reboot you can edit the
file /etc/udev/rules.d/20-names.rules and change the following line.

Change from:

KERNEL=="tun",               NAME="net/%k"

Change to:

KERNEL=="tun",               NAME="net/%k", GROUP="vboxusers", MODE="0660"

---

### Post by freackout on 2008-07-09
> **kell_pt said:**
> This exactly what I'm trying to do... insofar I haven't managed to reach any solution. Anyone has any ideas on this?

see this link for help on bridge for the guest ie keeps them static.
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

