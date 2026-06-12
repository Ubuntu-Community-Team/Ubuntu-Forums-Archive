---
title: "Ubuntu Netwokring"
date: 2016-07-29
forum: Virtualisation
---

### Post by vpandiri on 2016-07-29
[COLOR=#111111][FONT=Ubuntu]I have configured in my virtual box network bridge adapter of guest Ubuntu, so I could ssh to it from the host machine.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The problem is that the guest Ubuntu ip address keep changing.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Even though it changes within a very short range 192.168.0.4-10 it is still takes time to configure Putty and other programs each time.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My Internet service provide also DHCP.

Is there a way to make the guest Ubuntu ip address to be static?

My guest OS has the full GUI.

Even i tried this process no use.

Edit /etc/network/interfaces to reflect something like this:[/FONT][/COLOR]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address **192.168.0.X**
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway **192.168.0.X**
dns-nameservers **192.168.0.X**[COLOR=#111111][FONT=Ubuntu]




[/FONT][/COLOR]

---

### Post by howefield on 2016-07-29
Better to set the static IP for the machine in the router if you can ?

---

### Post by vpandiri on 2016-08-01
its not possible for setting Static IP.

---

### Post by howefield on 2016-08-01
Thread moved to the "*Virtualisation*" forum.

---

### Post by Bucky Ball on 2016-08-01
What is preventing you from setting a static IP address? You set it on your local machine via the Network Manager icon> Edit Connections. You are not the owner/administrator of the router?

If you do not set a static IP, yes, the IP will keep changing as a new one is being served by the router/access point everytime you restart the machine. Unless you set a static IP outside of the range the router's DHCP server is serving IPs in, changing IPs will continue to be a problem.

---

### Post by MAFoElffen on 2016-08-03
Please return to your first post: Edit> Advanced Edit > Select the text of your files and/or commands > Select the "#" icon to surround the selected text inside code tags. A forums policy, and makes that easier to read. (Besides not running the risk of the forums software painstakingly misinterpreting something.)

Edited from your post
> **vpandiri said:**
> ...
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address **192.168.0.X**
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway **192.168.0.X**
dns-nameservers **192.168.0.X**[COLOR=#111111][FONT=Ubuntu]
.[/FONT][/COLOR]
Here is what I would do first
```

sudo lshw -class network
ls /sys/class/net
ip -o link show | awk '{print $2,$9}'
cat /proc/net/dev

```
That will show your virtualized network devices and what states they are in. That will indicate what it going on in the first 3 layers of the network layers. That will also verify that your first wired connection is name eth0.

If your first device is verified as eth0, then 
(By most ips'es modem/routers setups)
```

# Edited /etc/network/interfaces file

# Local 
auto lo
  iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
  address 192.168.0.4
  netmask 255.255.255.0
  network 192.168.0.0
  broadcast 192.168.0.255
  gateway 192.168.0.1
  dns-nameservers 192.168.0.1

```
If the device name is not eth0, then adjust that name to reflect.

EDIT-- Remember that this is your guest settings. If you temporarily set it to dhcp and query what the setting that dhcp server gave your guest, you can adjust your static setting to fall into that same network. Use your resources to diagnose and gather information.

On the other hand, if your set your VM guest temporarily to dhcp and you do not get a successful connection, then you have some problem on the host that you need to resolve first.

---

