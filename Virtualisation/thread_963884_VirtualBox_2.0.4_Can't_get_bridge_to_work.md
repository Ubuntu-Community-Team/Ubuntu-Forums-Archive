---
title: "VirtualBox 2.0.4 Can't get bridge to work"
date: 2008-10-30
forum: Virtualisation
---

### Post by endfx on 2008-10-30
Hi, I've just installed virtualbox 2.0.4 on Ubuntu 8.04.

Problem is, I can't seem to get bridge networking setup.
I've done the following

1) Installed bridge-utils
2) Added the following into /etc/network/interfaces:
auto br0 
iface br0 inet dhcp
    bridge_ports eth0
3) Added the line "vbox0 myusername br0" to /etc/vbox/interfaces
4) /etc/init.d/networking restart
My br0 interface now get the IP address instead of eth0

5) Network settings in my vm:
Adapter type: pcnet-fast III (am79c973)
Attached to: Host interface
Interface Name: vbox0

When I boot into my guest OS (ubuntu 8.04 Server) I don't get any dhcp offers.

Can anybody offer my any suggestions? 

Thanks.

---

### Post by mr_e_dub on 2008-11-04
bump...  same story on Intrepid...

---

### Post by rcrcomputing on 2008-11-04
This is how I do it. No scripts etc..   just an entry in the /etc/network/interfaces file. Works for me in hardy and/or intrepid.

[http://programs.rcrnet.net/]("http://programs.rcrnet.net/")

Click on Linux bridge

---

### Post by jokker on 2008-11-05
Intrepid ignores the file /etc/network/interfaces so I don't know how I could setup a bridge in this file... What file should be used on intrepid please ?

---

### Post by rcrcomputing on 2008-11-05
> **jokker said:**
> Intrepid ignores the file /etc/network/interfaces so I don't know how I could setup a bridge in this file... What file should be used on intrepid please ?
Oops, I failed to mention, You may wish uninstall network-manager as I do not need, nor want it. If I'm going to take control of my network settings, I do not want network-manager jacking with it. :)

---

### Post by jokker on 2008-11-05
I'm trying this right now but this is not working. after purge network-manager network-manager-gnome and editing interfaces file I rebooted but I do not have dns working... I do have connectivity though, I can ping my router, but it won't let me get out (seems like resolv.conf is ignored this time). This is the problem I ran into for the last 5 days. It looks like my system really needs network-manager to have dns working.

edit= resolv.conf was empty, I edited it but no more luck, this time at reboot MTA takes about three minutes to sart... and no DNS neither !

---

### Post by rcrcomputing on 2008-11-05
> **jokker said:**
> I'm trying this right now but this is not working. after purge network-manager network-manager-gnome and editing interfaces file I rebooted but I do not have dns working... I do have connectivity though, I can ping my router, but it won't let me get out (seems like resolv.conf is ignored this time). This is the problem I ran into for the last 5 days. It looks like my system really needs network-manager to have dns working.

edit= resolv.conf was empty, I edited it but no more luck, this time at reboot MTA takes about three minutes to sart... and no DNS neither !

Ok, let's slow down a bit. Now that you have network manager uninstalled, you can get your network up and running with dhcp just to make sure everything is working before you go futher.

in resolve.conf you will have something like this. (change the ip address's to the right ones for you.

######################
search your.domain
nameserver 192.168.0.1
nameserver 12.5.224.226
######################

Now, in /etc/network/interfaces

######################
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
######################

That should work

After that works, you can try the tap. Note, you will have to reboot after putting the taps in your interfaces file.

Hope this helps..

---

### Post by jokker on 2008-11-05
No thanks, I do NOT want dhcp on this machine, it MUST be static. I have 2 NICs in this machine, 2 gigabit. eth0 MUST be 192.168.0.22 and eth1 192.168.0.21 and will be the bridge for 4 virtual machines
so here is my interfaces file for you to understand:

auto lo
iface lo inet loopback

## eth0
auto eth0
iface eth0 inet static
        address 192.168.0.22
                                hwaddress ether 00:0f:b5:f9:30:bc
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

## Original eth1
#auto eth1
#iface eth1 inet static
#        address 192.168.0.21
#                               hwaddress 00:12:17:54:ee:c4
#        netmask 255.255.255.0
#        network 192.168.0.0
#        broadcast 192.168.0.255
#        gateway 192.168.0.1



## Virtual interfaces for bridged VirtualBox network

# Taps should be before br0
auto tap0
iface tap0 inet manual
tunctl_user david
uml_proxy_arp 192.168.0.30
uml_proxy_ether eth1

aauto tap1
iface tap1 inet manual
tunctl_user david
uml_proxy_arp 192.168.0.31
uml_proxy_ether eth1

auto tap2
iface tap2 inet manual
tunctl_user david
uml_proxy_arp 192.168.0.32
uml_proxy_ether eth1

auto tap3
iface tap3 inet manual
tunctl_user david
uml_proxy_arp 192.168.0.33
uml_proxy_ether eth1

auto tap4
iface tap4 inet manual
tunctl_user david
uml_proxy_arp 192.168.0.34
uml_proxy_ether eth1

## Actual bridge for eth1 to tapx virtual devices
# Ip address is the same as eth1 would have been.
auto br0
iface br0 inet static
address 192.168.0.21
                        hwaddress ether 00:12:17:54:ee:c4
netmask 255.255.255.0
gateway 192.168.0.1
bridge_ports eth1 tap0 tap1 tap2 tap3 tap4
bridge_maxwait 0

and no, you don't need to reboot, a network restart is enough. The only time you need to reboot a Unix system is when you change the kernel ;-)

---

### Post by rcrcomputing on 2008-11-06
I guess, I'm failing to understand what you are attempting to do. I had the assumption you had one nic and wanted the vm's to use that nic with ip's on the same net range. So I don't seen where a second nic comes in and have no idea to what the cable on the second nic is attached to.

You'd indicated after removal of network-manager, you had no dns, the above instructions were to simply get your internet working via dhcp to get you to a known good position before you proceed. Then you could make it static, again, before you moved on to bridging. Thus, proving to yourself, you do not need network-manager.

BTW, I'm well aware you don't HAVE to restart, but it is much easier for me to tell you to restart than it is to give you "brctl" commands to remove whatever bridges you have previously attempted to make that may be lurking around.

Lastly, I noticed you had a different ip address on your uml_proxy_arp lines than you do on your br0 to which the taps are attached. That simply won't work.

---

### Post by jokker on 2008-11-06
OK first of all thanks for your help.
eth0 is attached to a gigabit switch and out to the router, just like eth1 is. I used to have an ipcop installed on this machine and I just kept both NICs inside. I typically reserve eth1 for the virtual machines because two of the VMs will be "on" 24/7 and I like to keep the traffic separated. I also just edited the interfaces file and think it would be a good thing to post it again. In this state everything works including DNS to get out the router in the outside world, here is the file:


## Loopback
auto lo
iface lo inet loopback


## eth0  (gigabit #1 pci)
auto eth0
iface eth0 inet static
        address 192.168.0.22
	hwaddress ether 00:0f:b5:f9:30:bc
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
	dns-nameservers	68.105.28.12 68.105.29.12 68.105.28.11


## eth1 (gigabit #2 pci)
#auto eth1
#iface eth1 inet static
#	address 192.168.0.21
#	hwaddress ether 00:12:17:54:ee:c4
#	netmask 255.255.255.0
#	network 192.168.0.0
#	broadcast 192.168.0.255
#	gateway 192.168.0.1
#	dns-nameservers	68.105.28.12 68.105.29.12 68.105.28.11



## Virtual interfaces for bridged VirtualBox network
## Taps before bridge (br0)

#auto tap0
#iface tap0 inet manual
#tunctl_user david
#uml_proxy_arp 192.168.0.21
#uml_proxy_ether eth1

#auto tap1
#iface tap1 inet manual
#tunctl_user david
#uml_proxy_arp 192.168.0.21
#uml_proxy_ether eth1

#auto tap2
#iface tap2 inet manual
#tunctl_user david
#uml_proxy_arp 192.168.0.21
#uml_proxy_ether eth1

#auto tap3
#iface tap3 inet manual
#tunctl_user david
#uml_proxy_arp 192.168.0.21
#uml_proxy_ether eth1

#auto tap4
#iface tap4 inet manual
#tunctl_user david
#uml_proxy_arp 192.168.0.21
#uml_proxy_ether eth1

## Actual bridge from eth1 to tapx virtual devices ("bridge_ports ethx tapx")
# Ip address is the same as eth1 would have been.
#auto br0
#iface br0 inet static
#address 192.168.0.21
#hwaddress ether 00:12:17:54:ee:c4
#netmask 255.255.255.0
#broadcast 192.168.0.255
#network 192.168.0.0
#gateway 192.168.0.1
#bridge_ports eth1 tap0
#bridge_maxwait 0
#dns-nameservers	68.105.28.12 68.105.29.12 68.105.28.11


As you can see only eth0 is enabled, and this works just fine. If I enable eth1: no DNS. Even the original non-bridged eth1 won't give me internet (with the same eth0 enable). So even though one device is properly configured and works, the other one (eth1) will rot the other somehow, strange behavior on Intrepid ! Any help is much appreciated, thank you.

---

