---
title: "internet problems on virtualbox"
date: 2012-01-23
forum: Ubuntu Studio
---

### Post by najjems on 2012-01-23
Hi guys, I'm running Ubuntu Studio 11.04 as a guest OS on VirtualBox (Windows 7 as the host)  When I first installed it, my internet was working fine, but last night I was working on a networking/chat application  project for school, and I needed to set-up some virtual IP addresses.  One tutorial required me to purge 'network manager', and although it did work for me, upon shutting down and starting up the next day, I found that I have no internet connection on my Ubuntu anymore. I think it might have something to do with me purging 'network manager'  i have no way of installing it again since I have no internet. :/  


results of ifconfig -a

[[IMG]http://img.photobucket.com/albums/v256/hp_witch/ifconfig-a.png[/IMG]]("http://smg.photobucket.com/albums/v256/hp_witch/?action=view&current=ifconfig-a.png")




[[IMG]http://img.photobucket.com/albums/v256/hp_witch/connectionproperties.png[/IMG]]("http://smg.photobucket.com/albums/v256/hp_witch/?action=view&current=connectionproperties.png")  


hope someone can help me through this! thanks!

---

### Post by jejeman on 2012-01-23
If you removed network manager, then you need to set network manualy.
[https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)

---

### Post by najjems on 2012-01-23
[SIZE=2][SIZE=3]okay, thanks for the link. it sort of helped, well now eth0 shows when i run 'ifconfig'

still doesn't have internet though, i'm not sure about what i did...[/SIZE]
[/SIZE]
> i ran '[FONT=Courier New]*gksu gedit	  *[/FONT][FONT=Courier New]*/etc/network/interfaces*[/FONT]'
[SIZE=2]>[/SIZE][FONT=Verdana][SIZE=2] [/SIZE][/FONT][FONT=Verdana][SIZE=3]added this to the file[/SIZE][/FONT]

[I]auto eth0 iface eth0 inet dhcp
[/I]
  ~The second line means that interface (“iface”) eth0,  	  should have an IPv4 address space (replace “inet” with  	  “inet6” for an IPv6 device)
[FONT=Verdana][SIZE=3] how do i know if my device is IPv4 or 6?[/SIZE][/FONT]


Assuming your network and DHCP server are properly configured, 
this machine's network should need no further configuration to operate properly.  
[FONT=Verdana][SIZE=3]
well i don't know if it is properly configured. :([/SIZE][/FONT]

The DHCP server will provide the default gateway 
(implemented via the **route** command), the device's IP address 
(implemented via the **ifconfig** command), and DNS servers used on the network 
(implemented in the /etc/resolv.conf file.)


	  To configure your Ethernet device with a static IP address and custom  	  configuration, some more information will be required.  Suppose you want to  	  assign the IP address	192.168.0.2 to the device eth1, with the typical netmask  	  of 255.255.255.0.  Your default gateway's IP address is 192.168.0.1.  You would  	  enter something like this into /etc/network/interfaces: 	  
*iface eth1 inet static 	address 192.168.0.2 	netmask 255.255.255.0 	gateway 192.168.0.1* 
[SIZE=3]

~so i can assign any IP address i want? how will i know my gateway's IP add?[/SIZE]

---

### Post by jejeman on 2012-01-23
I don't know what you are trying to do, but for vbox most common case its better to use dhcp. This is just what you need.
```
auto eth0
iface eth0 inet dhcp
```For any special configuration read the Virtualbox help. Vbox devices are ipv4.

---

