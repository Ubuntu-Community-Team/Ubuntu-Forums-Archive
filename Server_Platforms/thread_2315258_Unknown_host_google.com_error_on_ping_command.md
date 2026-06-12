---
title: "Unknown host google.com error on ping command"
date: 2016-02-27
forum: Server Platforms
---

### Post by nnamdi3 on 2016-02-27
Hello Guys, 
I am new to Ubuntu server 14 LTS. 

1) I have just completed the installation of Ubuntu server 14 LTS on Virtualbox and have changed my IP to static IP. Using the following settings

address 192.168.0.24
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 192.168.0.1

2) I have reboot my server to refresh the network setting then I discovered a message during the booting proccess, "booting without full network configuration"

3) I also tried to ping google.com to check for network but I can only receive this message "Unknown host google.com"

Please someone should help me
Thanks

---

### Post by howefield on 2016-02-27
Thread moved to the "*Server Platforms*" forum.

---

### Post by MAFoElffen on 2016-02-27
since you said on "ping", let's explore that. Please post the result of:
```

ping -c 3 127.0.0.1    # to local host
ping -c 3 192,168.0.24    # to it's own NIC
ping -c 3 -R -v 192.168.0.1    # to the gateway, Record route and get verbose ICMP
ping -c 3 8.8.8.8    # to numeric IP at google
ping -c 3 www.google.com  # to google through dns

```

If you have problems with your dns on the last one, explore further using
```

nslookup www.google.com
traceroute www.google.com

```
If you got a ping to 8.8.8.8 but not to [www.google.com]("http://www.google.com"). you  are having problems with dns. You currently have that pointed to your gateway/router... Not all routers offer dns as a service. Try to change this line in your interfaces file:
```

dns-nameservers 8.8.8.8 8.8.8.4

```
Which is the public dns servers of google.

---

### Post by darkod on 2016-02-27
As the previous post suggests (among its many commands :) ), always try ping 8.8.8.8 too, to check if you have internet at all.

It's surely a problem of the VM settings, or the subnet you are trying to use.

1. You know for sure your home LAN is 192.168.0.x right? And your router is 192.168.0.1 and it has dns running on it?

2. For that config to work, you need to set the network adapter settings on the VM to Bridge mode. Did you do that? If it's set to NAT mode it does not connect to your home LAN directly, it has the VBox NAT in between. That's why I always use Bridge mode too and I can assign LAN IPs directly to the VMs.

---

### Post by MAFoElffen on 2016-02-27
Sorry, I missed that it was a VM... for a test, if you comment out your static settings in interfaces and temporarily pont to dhcp, then do ifconfig, that should show you the network id (NID) that VM is located on, or if you are having a bridge problem between NID's.

If your end up with an ARPA address range, then you don't have access to dhcp, and should check your VM Host settings.

---

### Post by nnamdi3 on 2016-02-27
Hi, thanks for the quick response. I have used the dns-nameservers conf you gave me, it still displays "server starting without full network configuration". can you please tell me what the full network configuration is? Thanks

---

### Post by nnamdi3 on 2016-02-27
I tried to ping 8.8.8.8

reply
Network is unreachable

---

### Post by steeldriver on 2016-02-27
Did you set up the VM networking in NAT mode (the default, IIRC) or bridged mode?

IIRC in NAT mode, VirtualBox defaults to a 10.0.x.x address range - so trying to set a static address in 192.168.x.x isn't going to work

OTOH if you are trying to add your server to an existing LAN in the 192.168.x.x range, you will need to make sure the VM is configured for bridged mode

Either way, the simplest first step might be to set it back to pure DHCP and see what host address gets assigned to it (using ifconfig). You should then be able to use that as a basis for your static address parameters. Chances are you will get a DHCP-assigned DNS nameserver as well (either from the VirtualBox NAT adapter, or from your LAN's router / DHCP server if in a bridged configuration).

---

