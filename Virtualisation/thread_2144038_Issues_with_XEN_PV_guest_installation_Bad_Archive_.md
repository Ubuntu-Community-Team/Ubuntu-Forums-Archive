---
title: "Issues with XEN PV guest installation: Bad Archive error"
date: 2013-05-10
forum: Virtualisation
---

### Post by Ignado on 2013-05-10
Hello. I am very new to xen and just recentley set up Xen on Ubuntu server 12.04. I did a guided partition with LVM and followed the instructions on [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen). The installation went find and the server is up and running nicely. Everything went fine until i tried to install my PV guest. I just used the basic guid on the link i posted for manually installing a PV guest. During the creation of the vm the ubuntu installer says my archive link is bad. I am just using the standard united states archive. My settings are as follows:

/etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto xenbr0
iface xenbr0 inet static
    address xxx.32.92.xx
    netmask 255.255.255.192
    network xxx.32.92.0
    broadcast xxx.32.92.xx
    gateway xxx.32.92.x
        bridge_ports eth0
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp off


```

where the xxx's, in reality, have the proper numbers in them.

/etc/xen/vm01.cfg

```

name = 'vm01'
disk = ['phy:/dev/cis-du01/vm01,xvda,w']
vif = ['mac=78:2b:cb:43:39:8e,bridge=xenbr0']

kernel = "/var/lib/xen/images/ubuntu-netboot/vmlinuz"
ramdisk = "/var/lib/xen/images/ubuntu-netboot/initrd.gz"
extra = "debian-installer/exit/always_halt=true -- console=hvc0"

```

and the mac address is found from running ifconfig. And finally we have

/etc/xen/xend-config.sxp

```


# Random stuff
(dom0-min-mem 1024)
(enable-dom0-ballooning yes)
(total_available_memory 0)
(dom0-cpus 0)
(vncpasswd '')

# Network stuff
(xend-http-server yes)
(xend-unix-server yes)
(network-script network-bridge)
(network-script 'network-bridge netdev=eth0')
(network-script 'network-bridge bridge=xenbr0')
(vif-script vif-bridge)


```

For a little more description i run:

```
sudo xm create /etc/xen/vm01.cfg -c

```
Ubuntu fails to find my network so i set it up manually. I then input my ip-address, netmask and my broadcast as it apears in my /etc/network/interface file. 
It then tells me it is connecting to eth0 and then asks me to select my mirror to download the archive. I then select the united states mirror, it sits at 0% downloaded for a bit before it jumps to 100% and then it tells me bad archive. As a side note i should mention Dom0 is connected to the network just fine and ssh works without a problem. I have actually been trying to do these installs through ssh. 
Thanks for your help!!!

Output of ifconfig:

```

eth0      Link encap:Ethernet  HWaddr 78:2b:cb:43:39:8e  
          inet6 addr: fe80::7a2b:cbff:fe43:398e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:60879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4897877 (4.8 MB)  TX bytes:202607 (202.6 KB)

eth1      Link encap:Ethernet  HWaddr 78:2b:cb:43:39:8f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth2      Link encap:Ethernet  HWaddr 00:10:18:ac:7d:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth3      Link encap:Ethernet  HWaddr 00:10:18:ac:7d:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth4      Link encap:Ethernet  HWaddr 00:10:18:ae:6a:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth5      Link encap:Ethernet  HWaddr 00:10:18:ae:6a:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4898 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:372208 (372.2 KB)  TX bytes:372208 (372.2 KB)

xenbr0    Link encap:Ethernet  HWaddr 78:2b:cb:43:39:8e  
          inet addr:xxx.32.92.xx  Bcast:xxx.32.92.xx  Mask:255.255.255.192
          inet6 addr: fe80::7a2b:cbff:fe43:398e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59047 errors:0 dropped:31187 overruns:0 frame:0
          TX packets:943 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3540536 (3.5 MB)  TX bytes:176424 (176.4 KB)



```

---

### Post by tgalati4 on 2013-05-11
There are 67 US mirrors, which one did you pick?  You have to put a specific mirror IP address in the PV creation instructions.

---

### Post by Ignado on 2013-05-11
> **tgalati4 said:**
> There are 67 US mirrors, which one did you pick?  You have to put a specific mirror IP address in the PV creation instructions.

I am prompted to select a region. I select United States. It then shows up at this screen: 
[IMG]http://i.imgur.com/e11w2Qv.png[/IMG]
which us.archive.ubuntu.com. After clicking enter I end up on this screen:
[IMG]http://i.imgur.com/wLbrOcT.png[/IMG]
Hope this makes it more clear.

---

### Post by heiko_s on 2013-05-12
> **Ignado said:**
> Hello. I am very new to xen and just recentley set up Xen on Ubuntu server 12.04. I did a guided partition with LVM and followed the instructions on [https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen). The installation went find and the server is up and running nicely. Everything went fine until i tried to install my PV guest. I just used the basic guid on the link i posted for manually installing a PV guest. During the creation of the vm the ubuntu installer says my archive link is bad. I am just using the standard united states archive. My settings are as follows:
...

/etc/xen/vm01.cfg

```

name = 'vm01'
disk = ['phy:/dev/cis-du01/vm01,xvda,w']
vif = ['mac=78:2b:cb:43:39:8e,bridge=xenbr0']

kernel = "/var/lib/xen/images/ubuntu-netboot/vmlinuz"
ramdisk = "/var/lib/xen/images/ubuntu-netboot/initrd.gz"
extra = "debian-installer/exit/always_halt=true -- console=hvc0"

```

and the mac address is found from running ifconfig. And finally we have

/etc/xen/xend-config.sxp

```


# Random stuff
(dom0-min-mem 1024)
(enable-dom0-ballooning yes)
(total_available_memory 0)
(dom0-cpus 0)
(vncpasswd '')

# Network stuff
(xend-http-server yes)
(xend-unix-server yes)
(network-script network-bridge)
(network-script 'network-bridge netdev=eth0')
(network-script 'network-bridge bridge=xenbr0')
(vif-script vif-bridge)


```


**...and the mac address is found from running ifconfig ???** - what MAC address are you using in the vm config file?
```
name = 'vm01'
disk = ['phy:/dev/cis-du01/vm01,xvda,w']
vif = ['mac=78:2b:cb:43:39:8e,bridge=xenbr0']
...
```

**You cannot use an existing (= real hardware) MAC address in your vif = configuration !!!** You are using the MAC address of your eth0 interface - this is wrong! Your guest connects to the virtual bridge (xenbr0), in which case you have to specify a virtual MAC address (actually, you don't need to specify a MAC address at all, Xen will select a random one for you). Edit your vm01 config file and enter the following vif statement (pay attention to the MAC address):
```
vif = [ 'mac=00:16:3e:68:01:01,bridge=xenbr0' ]
``` You can change the 01:01 part to suit your needs. If you have several VMs running on your machine/network, you should specify a MAC address and make sure to change the 01:01 part to 01:02, 01:03, etc., else you will be in trouble. In fact, it may be good practice to use 01:01, 02:01 for different virtual bridges (or different PCs), and 01:01, 01:02, etc. for different VMs/virtual ports on the same virtual bridge. The 00:16:3e:68 MAC address part has been reserved by Xen for the purpose of creating virtual MAC addresses.


Next I would edit the /etc/network/interfaces file:

1. Comment out auto eth0 and iface eth0... (see below).
2. Add
```
dns-nameservers 8.8.8.8
``` to the auto xenbr0 section (see below).
3. Change netmask 255.255.255.192 to netmask 255.255.255.0 (unless you know that .192 will work!)
4. Unless you are totally sure about the network xxx.32.92.0 line, comment it out.

Save and restart networking, then give it a try.

Here the modified /etc/network/interfaces file:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet manual

auto xenbr0
iface xenbr0 inet static
    address xxx.32.92.xx
    netmask 255.255.255.0
#    network xxx.32.92.0
    broadcast xxx.32.92.xx
    gateway xxx.32.92.x
    dns-nameservers 8.8.8.8
        bridge_ports eth0
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp off


```

Explanations:
1. You have a bridged network, so dom0 and every domU connect to the bridge. You don't configure eth0 as the primary network interface, as we use the xenbr0 bridge for the networking. The bridge will use eth0 as the network port (see  bridge_ports eth0).
2. In case your PC doesn't resolve names - dns-nameservers 8.8.8.8 should solve that.
3. I would have to look up using network masks, but if any of your masks are incorrect, it won't work. My suggestion is to stick to the most common options, such as netmask 255.255.255.0 and without the network xxx.32.92.0 option, and play with them once you got everything working.

It may not be related to your error, but I would also edit the /etc/xen/xend-config.sxp file and get the settings somewhat in line with this [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013#p628911]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013#p628911"). If you want to use virt-manager, you need xend-unix-server yes. The Xen documentation discourages the use of the xend network scripts (see the link for more on network configuration), I believe (network-script /bin/true) is the option.

Here is my xend-config.sxp file for reference:
```
#(xend-http-server no)
(xend-unix-server yes)
(network-script /bin/true)
(vif-script vif-bridge)
(dom0-min-mem 1024)
(enable-dom0-ballooning no)
(total_available_memory 0) # You may need to change that!
(dom0-cpus 0)
(vncpasswd '')
#(keymap 'en-us') # You may want to specify this

```

Yeah, Xen can be a little challenging at the beginning. Hope this solves the issue. Good luck!

---

### Post by Ignado on 2013-05-14
Thanks for the help!! Unfortuantley I still am runing into the same issue. Still looking for a solution.

> **heiko_s said:**
> **...and the mac address is found from running ifconfig ???** - what MAC address are you using in the vm config file?
```
name = 'vm01'
disk = ['phy:/dev/cis-du01/vm01,xvda,w']
vif = ['mac=78:2b:cb:43:39:8e,bridge=xenbr0']
...
```

**You cannot use an existing (= real hardware) MAC address in your vif = configuration !!!** You are using the MAC address of your eth0 interface - this is wrong! Your guest connects to the virtual bridge (xenbr0), in which case you have to specify a virtual MAC address (actually, you don't need to specify a MAC address at all, Xen will select a random one for you). Edit your vm01 config file and enter the following vif statement (pay attention to the MAC address):
```
vif = [ 'mac=00:16:3e:68:01:01,bridge=xenbr0' ]
``` You can change the 01:01 part to suit your needs. If you have several VMs running on your machine/network, you should specify a MAC address and make sure to change the 01:01 part to 01:02, 01:03, etc., else you will be in trouble. In fact, it may be good practice to use 01:01, 02:01 for different virtual bridges (or different PCs), and 01:01, 01:02, etc. for different VMs/virtual ports on the same virtual bridge. The 00:16:3e:68 MAC address part has been reserved by Xen for the purpose of creating virtual MAC addresses.


Next I would edit the /etc/network/interfaces file:

1. Comment out auto eth0 and iface eth0... (see below).
2. Add
```
dns-nameservers 8.8.8.8
``` to the auto xenbr0 section (see below).
3. Change netmask 255.255.255.192 to netmask 255.255.255.0 (unless you know that .192 will work!)
4. Unless you are totally sure about the network xxx.32.92.0 line, comment it out.

Save and restart networking, then give it a try.

Here the modified /etc/network/interfaces file:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet manual

auto xenbr0
iface xenbr0 inet static
    address xxx.32.92.xx
    netmask 255.255.255.0
#    network xxx.32.92.0
    broadcast xxx.32.92.xx
    gateway xxx.32.92.x
    dns-nameservers 8.8.8.8
        bridge_ports eth0
    bridge_fd 9
    bridge_hello 2
    bridge_maxage 12
    bridge_stp off


```

Explanations:
1. You have a bridged network, so dom0 and every domU connect to the bridge. You don't configure eth0 as the primary network interface, as we use the xenbr0 bridge for the networking. The bridge will use eth0 as the network port (see  bridge_ports eth0).
2. In case your PC doesn't resolve names - dns-nameservers 8.8.8.8 should solve that.
3. I would have to look up using network masks, but if any of your masks are incorrect, it won't work. My suggestion is to stick to the most common options, such as netmask 255.255.255.0 and without the network xxx.32.92.0 option, and play with them once you got everything working.

It may not be related to your error, but I would also edit the /etc/xen/xend-config.sxp file and get the settings somewhat in line with this [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013#p628911](http://forums.linuxmint.com/viewtopic.php?f=42&t=112013#p628911). If you want to use virt-manager, you need xend-unix-server yes. The Xen documentation discourages the use of the xend network scripts (see the link for more on network configuration), I believe (network-script /bin/true) is the option.

Here is my xend-config.sxp file for reference:
```
#(xend-http-server no)
(xend-unix-server yes)
(network-script /bin/true)
(vif-script vif-bridge)
(dom0-min-mem 1024)
(enable-dom0-ballooning no)
(total_available_memory 0) # You may need to change that!
(dom0-cpus 0)
(vncpasswd '')
#(keymap 'en-us') # You may want to specify this

```

Yeah, Xen can be a little challenging at the beginning. Hope this solves the issue. Good luck!

---

### Post by heiko_s on 2013-05-14
When you open Firefox in the PV guest, do you get an Internet connection?

---

### Post by Ignado on 2013-05-15
> **heiko_s said:**
> When you open Firefox in the PV guest, do you get an Internet connection?

I can not open Firefox in my PV guest as it has no operating system installed. Unless there is a way to do so that I dont know about. In Dom0 I can access firefox and ping google and some other random websites. 

I had my set up identical to you told me. When that did work I also tried a variety of combinations of the netmask you gave me as well as mine. And also I should mention I typically do these installs in SSH. I have only done it a handful of times on the server itself.

---

### Post by heiko_s on 2013-05-16
Sorry, I'm getting senile. Here is what you can try now:

1. First make sure you configured the /etc/network/interfaces file as specified in the link you posted (using dhcp), or with static IP as I wrote. You can comment out all the bridge_... except the bridge_ports eth0 line.
2. Your ifconfig output shows 6 Ethernet interfaces??? Do you really have that many NICs? It seems a little strange. If you don't have that many NICs, you may have to take care of that.
3. Make sure you enabled networking:
```
sudo /etc/init.d/networking restart
```

4. Make sure you got the (xend-unix-server yes) in /etc/xen/xend-config.sxp, then install virt-manager. Run
```
sudo xm new /etc/xen/vm01.cfg
sudo virt-manager
```

Your new vm01.cfg domain should appear in the virt-manager screen. Click the console icon, then the button on the right for information. You can check your configuration, edit or add things. When all looks good, press the run button.


To remove the guest entry from the virt-manager screen, enter in a terminal:
```
sudo xm delete vm01
```

Instead of using sudo xm new /etc/... you can also use the create button in virt-manager. 

Another option is to install Ubuntu as a HVM guest and then convert it to a PV guest, or use the PVHVM drivers. I need to go now, but there should be more info on the net.

---

