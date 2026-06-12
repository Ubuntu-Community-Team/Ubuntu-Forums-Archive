---
title: "Need help with ifup and ifdown commands (new, sorry)"
date: 2017-08-21
forum: Server Platforms
---

### Post by xaned2 on 2017-08-21
So I just installed Ubuntu(16.04LTS) onto a pc of mine a couple days back. Seemed like a decent installation for a pc with NO internet connection, because for some reason, I thought tools for wireless network adapters came with lol. 

The problem here is I can't use ifdown to bring an interface down due to the following error: "ifdown: *given interface* is not configured"
I had the following in my configuration file (the file being /etc/network/interfaces of course):
auto enp5s0
iface enp5s0 inet static 
address 192.168.x.x
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.254
dns-nameserver x.x.x.x

Really want it to stay as a static ip, planing on hosting websites on this thing.
I did the lshw -c network search, and the interfaces are "working", I say this because they were disabled yesterday and I got them back up, somehow. I sadly forgot how I did it  

(The first config is for my ethernet interface, the second is for a wireless interface that i'm not going to add, because it's not going to work period due to not having the wlan package installed)

Yet it still wouldn't let me use ifdown, nor ifup correctly (It would work, but the changes made in the config file wouldn't got through). I can use the --force option to bring a given interface up and down, but the configurations made still wouldn't go through :(
I can't connect to the internet at all because of this problem. Due to the interfaces some how not wanting to be configured.

I also tried the sudo ifconfig *interface* up/down command(s), still no changes to the interface.
The result is usually: 

RTNETLINK answers: File exists
Failed to bring up enp5s0(the interface) 

Really annoying, for a dude who really wants to get into network administration, but can't get something as "simple" as this working.

(I now have an Ethernet cable lol)

---

### Post by darkod on 2017-08-21
Delete the 'network' and 'broadcast' from the interfaces file. They are not needed (they are calculated from address and netmask values) and can only create confusion if used wrongly. In your case the broadcast value is wrong for example. If you LAN is 192.168.0.0/24 then the broadcast is last address in it, 192.168.0.255. Not 192.168.0.254 as in your file.

And you are missing a 'gateway' parameter. You need it for static IP setup.
And the dns parameter is 'dns-nameservers'.

If you don't mind doing the installation again, I would recommend reinstalling this time connected to the internet. During installation I think it also configures some stuff for apt-get that are not executed if there is no internet connection. Since you just installed and you have no data on the server, reinstalling takes less than half an hour and is probably the best way forward.

---

### Post by xaned2 on 2017-08-21
I'll do that now, thanks for the reply

---

### Post by xaned2 on 2017-08-21
Alright, everything looks great so far. Just reinstalled with internet this time lol, and everything seems to be working perfectly. Turns out, I must've set the wireless interface as a primary interface, and since no wlan packages were installed, I couldn't configure the interface so that I could gain access the web. Thanks for the help :D

---

### Post by darkod on 2017-08-21
No problem. If you don't need any further help, you can mark this as solved. You can do that in Thread Tools above the first post.

---

