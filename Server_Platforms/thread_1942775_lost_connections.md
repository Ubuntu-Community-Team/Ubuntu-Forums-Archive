---
title: "lost connections"
date: 2012-03-18
forum: Server Platforms
---

### Post by Mit21 on 2012-03-18
I working on setting up a server (ubuntu 10.04) in virtual box 

After the install i can do 2 steps before get in to trouble 
set the two nic to static ip eth0 192.168.123.120 and eth1 172.16.0.1)  note: in virtual  box the eth stands on bridged and host only
After putting the static ip in i restart the networkservices (  /init.d/network restart) 
this succeed  

Now i want to install openssh. (apt-get install openssh)
the first time the install of the openssh did not succeed and asked for update. Thus I  did apt-get update After the reboot the network connections are gone (the network  connection in the interface is empty) 
A second try i didn't need to do the update but after a while i've got the same problems

i tried following steps to get the connections back:

restart of the network services (/etc/init.d/network restart) 
result: rtnetlink: no such process 
found a solution by starting eth0 and eth1. the network services return but there is still no  connection.
ping to the gw 192.168.123.1 > unreachable 
ping 127.0.0.1 > okay 
ifconfig > no errors, everything seem up and running  I the machine has once more established again same problem after reboot. 

netstat, int and ifconfig in attach

---

### Post by Holdolin on 2012-03-18
apt-get update updates your repository info, if you want to upgrade your software, it's apt-get upgrade

---

### Post by Mit21 on 2012-03-19
the upgrade isn't the problem.

i'm putting the interface to static ip and then i lose my connections

Does anyone have an idea why the connections stopped?

---

### Post by Mit21 on 2012-03-23
It seems to a problem with the network manager.

To solve it disable network manager with
sudo apt-get remove network-manager network-manager-gnome

---

### Post by spynappels on 2012-03-23
Did you install Ubuntu Server Edition and add the desktop or did you simply install Ubuntu Desktop? Server edition is not supposed to use Network Manager, you set it up by editing /etc/network/interfaces

---

### Post by Mit21 on 2012-03-24
i was using the linux desktop with webmin

---

### Post by dharmavir on 2012-03-24
Here, as you're using virtual-box lot of things depends on how you're trying to configure virtual-network with virtual-box and vm-node. There few options NAT / Host-only / Bridged / Internal / Generic. Either NAT or Bridged should work, bridged will give direct access to your network adepter and you will be able to assign fixed static-local-ip from your network.

To change IP address of a machine manually:[COLOR=#000000][FONT=Tahoma][FONT=Lucida Console]

[/FONT][/FONT][/COLOR]
[FONT=Lucida Console] $ sudo vim /etc/network/interfaces[/FONT]
[FONT=Lucida Console] # change settings as you want:[/FONT]
[FONT=Lucida Console]-----------------------------------------------------------------------[/FONT]
[FONT=Lucida Console]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.95.4.101
        netmask 255.255.255.0
        network 10.95.4.0
        broadcast 10.95.4.255
        gateway 10.95.4.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 10.10.2.206 10.10.2.208
        dns-search surescripts.local
[/FONT]
[FONT=Lucida Console][COLOR=#000000][FONT=Tahoma][FONT=Lucida Console]-----------------------------------------------------------------------[/FONT][/FONT][/COLOR][/FONT]
[FONT=Lucida Console] $ sudo /etc/init.d/networking restart

Let me know if it still do not work out.

Good luck.
[/FONT]

---

