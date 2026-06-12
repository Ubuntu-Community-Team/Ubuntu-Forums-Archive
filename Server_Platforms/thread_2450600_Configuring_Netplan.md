---
title: "Configuring Netplan"
date: 2020-09-17
forum: Server Platforms
---

### Post by jarnold231 on 2020-09-17
Hi there, 

Just upgraded to 20.04 having had the server running 18.04 - I did a clean install. I also changed my router which came with a new subnet and I was hoping someone might be able to help me configure the Netplan to set a static IP.

The router IP is 192.168.3.1, with its WAN IP being 192.168.1.200 with the overall networks default gateway being 192.168.1.1

Realise this is probably more of a networking rather than Ubuntu specific question, but hope someone might be able to tell me if I need to use routing etc

```

[COLOR=#000000][FONT=Consolas]# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:    
ethernets:        
enp0s3:            
dhcp4: false            
addresses: [192.168.3.10/24]            
gateway4: 192.168.1.1            
nameservers:              
addresses: [8.8.8.8,8.8.4.4]            
routes:            
- to: 192.168.1.1/24              
via: 192.168.1.200[/FONT][/COLOR]
```

---

### Post by ameinild on 2020-09-17
I think you need to specifiy how you would like the setup to be.

Normally, your router would also be your default gateway - is there any reason this should not be the case here?

The netplan site has a number of examples of [routing configurations]("https://netplan.io/examples/#reaching-a-directly-connected-gateway") that you could also have a look at.

Also, a generic remark is that the netplan .yaml file needs proper indentation, which you do not have in the codeblock in your post (but maybe your file is ok).

---

### Post by jarnold231 on 2020-09-17
Hi ameinild

Structure should be:

server [192.168.3.10] > router [192.168.3.1] > wanIP [192.168.1.200] > external unifi router [192.168.1.1] > internet

understood and aware of proper indentation, my bad on editing my post.

---

### Post by TheFu on 2020-09-17
YAML is the config file format for netplan.  If you don't post using "code tags", we cannot help.
[https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168) explains **code tags** for this forum.

Please just edit the original post, OP, to use code tags.  Looks like you have, but had already screwed the formatting.  Code tags are simple select/paste operations on Unix X/Windows systems.  No need to touch fonts, sizes, colors, bold, or anything else, just wrap the code just like a "quote" or "bold" or "italics" tags.  The Advanced Editor has a button, if you need it, but most of the time, I just use the 'quote' button and manually change 'quote' into 'code'.

---

### Post by ameinild on 2020-09-17
> **jarnold231 said:**
> server [192.168.3.10] > router [192.168.3.1] > wanIP [192.168.1.200] > external unifi router [192.168.1.1] > internet


I still need to understand this setup, and why it has to be like this. 

Is this at home? A school? A company? Please provide a little more context.

Also, what is the reason you can't connect directly to the subnet provided by the Unifi router at 192.168.1.1 - what is the reason you want another router in between?

Again, normally you would "just" connect to your router (192.168.3.1) which is also your gateway/"default route", and this router will forward (NAT) the traffic to the next network and on to the internet. 

However, this looks like a "double NAT" setup, which might not be very efficient and cause problems. This is also why I ask the reason you need it this way? Thanks.

---

### Post by TheFu on 2020-09-17
192.168.3.10 doesn't need to know anything more than to use the gateway 192.168.3.1.
The router at 192.168.3.1 would have a gateway set to 192.168.1.1. 

That's the outbound NAT stuff.

Simple. No need for any extra netplan route additions.

It is any inbound connections that could get ugly, but that would only be due to routers usually having firewalls.

---

### Post by ameinild on 2020-09-17
Agree, so the netplan config in this case would be pretty textbook:

```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      dhcp4: false
      addresses: [192.168.3.10/24]
      gateway4: 192.168.3.1
      nameservers:
        addresses: [8.8.8.8, 8.4.4.8]

```

Also for future reference, I believe the statements 'gateway4:' and 'routes:' are mutually exclusive, since your 'gateway4' is the default route.
Still, be aware of the possible inherent problems in a double NAT setup like this.

---

### Post by TheFu on 2020-09-17
I'd add:
```
dhcp6: false
```
and disable IPv6 networking via grub too.  IPv6 is a huge security failure if your infrastructure doesn't know how to properly firewall and secure those connections.

Inside: /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"
```
Run **sudo update-grub** and reboot the box.  Too bad the old /etc/sysctl.conf methods don't work anymore. Just more things that systemd broke besides name resolution, the fstab, and easy ways to for an fsck on the root file system without console access.

---

