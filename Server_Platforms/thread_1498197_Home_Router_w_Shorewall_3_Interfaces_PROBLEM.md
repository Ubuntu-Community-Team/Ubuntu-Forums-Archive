---
title: "Home Router w/ Shorewall 3 Interfaces PROBLEM"
date: 2010-05-31
forum: Server Platforms
---

### Post by UncleAelfrich on 2010-05-31
I have a home Ubuntu router (10.04) that I have built that works fine as a router/firewall using Shorewall. It's current configuration is as follows:

eth0     "net" interface dynamic IP
eth1     "loc" interface static IP

behind eth1 I have several Windows 7 computers and an Ubuntu file/print server (9.10) running Samba.

I now want to add wireless to this setup. I have another network interface (eth2) that I want to connect to a Linksys WAP54G. I would prefer that wireless connections be assigned DHCP, and I want all computers (both wired and wireless) to be able to browse and share with each other (using Samba).

I can't seem to get it to work.

I don't care if the wireless and wired are on separate subnets or not, but I do want to be able to browse across the subnets if they are on different subnets.

I can't determine if:
- I want to bridge eth1 and eth2, or how to do it exactly
- I want to use dnsmasq to share between the interfaces
- I need to set up a DHCP server

I am pretty sure I DO NOT want to have to set up Samba as a Primary Domain Controller (PDC). I would rather keep the Windows machines using workgroups rather than domains. I guess I would need to run Samba as a WINS server.

Please advise me as to the way to go that will work and be the cleanest. Thanks.

---

### Post by capscrew on 2010-05-31
> **UncleAelfrich said:**
> I have a home Ubuntu router (10.04) that I have built that works fine as a router/firewall using Shorewall. It's current configuration is as follows:

eth0     "net" interface dynamic IP
eth1     "loc" interface static IP

behind eth1 I have several Windows 7 computers and an Ubuntu file/print server (9.10) running Samba.

I now want to add wireless to this setup. I have another network interface (eth2) that I want to connect to a Linksys WAP54G. I would prefer that wireless connections be assigned DHCP, and I want all computers (both wired and wireless) to be able to browse and share with each other (using Samba).

I can't seem to get it to work.

I don't care if the wireless and wired are on separate subnets or not, but I do want to be able to browse across the subnets if they are on different subnets.

I can't determine if:
- I want to bridge eth1 and eth2, or how to do it exactly
- I want to use dnsmasq to share between the interfaces
- I need to set up a DHCP server

I am pretty sure I DO NOT want to have to set up Samba as a Primary Domain Controller (PDC). I would rather keep the Windows machines using workgroups rather than domains. I guess I would need to run Samba as a WINS server.

Please advise me as to the way to go that will work and be the cleanest. Thanks.

I have a system that is pretty close to what you have.  I even have a WAP54G that provides access for my wireless devices to the LAN.

I believe you will find that you can either use the AP in the existing LAN via a switch.  This is how mine is set up.  Or you can connect the AP to eth2 via a switch (or X-over cable) on a different subnet.

If you use the first method everything will be network neighborhood should be available for browsing.  

If you use the second method you will be forced to be on a different subnet.  The 2 NIC's can't be part of the same subnet. You shouldn't have 2 interfaces to the same destination.  In this scenario you will need to set up a WINS server on one of the Ubuntu/Samba hosts.  WINS severs are really for used passing NetBIOS namespace between multiple TCP/IP subnets.

I'm not sure whether DDNSmasq can provide dhcp address pools for 2 subnets.  This would involve dhcp relay functionality.

My suggestion is to place the AP in the same subnet on eth1.  This is by far the simplest way.  This is exactly what the WAP545G was designed for.

---

### Post by UncleAelfrich on 2010-05-31
Thank you. I chose your first option, and I am able to get connectivity to the LAN through the WAP. However, for some reason, the DNS is not resolving on the wireless machines. I can ping the external DNS server using its IP address (208.67.222.222), but I can't access the internet any other way.

Any suggestions?

Thanks.

---

### Post by capscrew on 2010-05-31
> **UncleAelfrich said:**
> Thank you. I chose your first option, and I am able to get connectivity to the LAN through the WAP. However, for some reason, the DNS is not resolving on the wireless machines. I can ping the external DNS server using its IP address (208.67.222.222), but I can't access the internet any other way.

Any suggestions?

Thanks.
What steps did you used to set up the WAP?  Is the address of the WAP in the same subnet as the other hosts? Did you set a default gateway and subnet mask?

On the main setup page I named the device (ap1) set the addressing to ***static*** and provided: [LIST]
[*]IP Address = 192.168.1.blah
[*]Subnet Mask = 255.255.255.0
[*]Default Gateway = 192.168.1.otherblah
[/LIST]

My network is 192.168.1.0 /24 (255.255.255.0)

The next page is for the Wireless (RF) but if you can connect to the LAN then the wireless is working.

The other two tabs are just housekeeping containing administration and setup information display.

Let me know if this helps.

---

### Post by UncleAelfrich on 2010-05-31
I think this problem is SOLVED, but not really to my satisfaction. I have to use static ips on the wireless.

Now I have to worry about getting Xbox Live to sream via upnp.  aarrgghh!

---

### Post by capscrew on 2010-05-31
> **UncleAelfrich said:**
> I think this problem is SOLVED, but not really to my satisfaction. I have to use static ips on the wireless.

Glad to hear you have made progress.  You should be able to use the services of the DHCP server in you network.  The AP does not isolate them.  If the other hosts in your LAN can use DHCP then your wireless hosts should be able to also.  My wireless hosts specifically use DHCP for IP addressing.

Edit:  If you mean the AP itself, that can be static.  You only set it once and generally you should have 250+ IP addresses in the subnet to choose from.

> 

Now I have to worry about getting Xbox Live to sream via upnp.  aarrgghh!

This is something I know nothing about.

---

### Post by WinstonChurchill on 2010-06-01
> **UncleAelfrich said:**
> I think this problem is SOLVED, but not really to my satisfaction. I have to use static ips on the wireless.

Now I have to worry about getting Xbox Live to sream via upnp.  aarrgghh!
Getting UPNP to work with your XBox isn't very difficult. Just install upnpd:
```
sudo apt-get install linux-igd
```Then, edit the file at '/etc/default/linux-igd': you'll have to set the EXTIFACE and INTIFACE to match your setup (obviously, the internal inferface is your LAN, and the external is the Internet), and set the "ALLOW_MULTICAST" option to YES. Then just execute:
```
/etc/init.d/linux-igd start
```If you've done any IPTABLES modification, you'll have to set some additional options, but the documentation in /etc/upnpd.conf and /etc/default/linux-igd is pretty easy to understand. Also, if you've got multiple internal interfaces (multiple physical NIC's for your LAN), you'll probably have to run multiple upnpd processes - I have not ever tried this, but it seems like it should work...

---

