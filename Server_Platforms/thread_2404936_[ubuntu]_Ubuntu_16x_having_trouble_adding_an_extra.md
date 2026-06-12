---
title: "[ubuntu] Ubuntu 16x having trouble adding an extra IP to my server."
date: 2018-10-29
forum: Server Platforms
---

### Post by space-chimp on 2018-10-29
I run a vulture server with Plesk and purchased a second IP for the NS2. I followed their guide [https://www.vultr.com/docs/add-secondary-ipv4-address](https://www.vultr.com/docs/add-secondary-ipv4-address) but I can't get it to work.

When I open */etc/network/interfaces* This is what is already in it:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

#source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback


auto ens3
iface ens3 inet dhcp
iface ens3 inet6 auto

```
When I check ifconfig it will show the default IP and mask.

I added:
```

auto ens3
iface ens3 inet static
address 83.new.ip.98
netmask 255.255.255.255

```
Then run the command from their guide says it already exist which I'm guess is the default one and it doesn't show up in ifconfig either.

So I already know it's probably a super simple mistake but yeah, ubuntu noob here.

Can someone tell me the correct way :)

---

### Post by TheFu on 2018-10-30
Did you really get a 2nd IP or just a singe static IP?  Looks like the system was using a dhcp address, which would seem odd for a hosting setup to me.  Not exactly useful to run a server.

You are missing the gateway setting, the netmask is clearly wrong.  You'll want to learn basic networking ASAP, since network knowledge is the most important for securing a server. It isn't hard, but you do need to learn about subnetting.

If you have 2 static IPs, you can add the 2nd to a virtual interface.  I'd have to look up the naming for that, but you can do that yourself.

I'm assuming you are using 16.04. [https://ubuntuforums.org/showthread.php?t=2368932](https://ubuntuforums.org/showthread.php?t=2368932) appears to have an answer.  Searching for answers in these forums usually will find that someone else already asked and got an answer.

Beware that 18.04 changes the network config methods entirely.

---

### Post by slickymaster on 2018-10-30
Thread moved to **Server Platforms** for a better fit

---

