---
title: "Can't connect to the network"
date: 2018-05-31
forum: Virtualisation
---

### Post by rudy558 on 2018-05-31
Hello,

I'm running ubuntu 16.04 on vmware, my vm network adapter is set to share with my mac (I know mac isn't the best choice, I plan to get a pc in the fall)

I'm new to ubuntu, this forum, and posting to forums in general, so I'm sorry in advance if I do something wrong. 
I'm currently in an intro to Linux class and we are working on networking. I'm having problems with my system and can't get ahold of my professor. We've done some messing around with the network settings, but I reverted to an old snapshot so the settings would be back to normal. Unfortunately I didn't save the system state before reverting to the old snapshot. The snapshot I am using now doesn't seem to be able to connect to the network. I've tried the following commands (the results are listed in each sub bullet point)

[LIST]
[*]ping [www.google.com]("http://www.google.com")
[LIST]
[*]ping: unknown host [www.google.com]("http://www.google.com")
[/LIST]

[*]sudo apt-get install upgrade
[LIST]
[*]E: Unable to locate package upgrade
[/LIST]

[*]sudo apt-get install
[LIST]
[*]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/LIST]

[*]when I try to ping another ip address on my LAN
[LIST]
[*]connect: Network is unreachable
[/LIST]

[*]sudo /etc/init.d/networking restart
[LIST]
[*][ok] Restarting networking (via systemctl): networking.service.
[*]If I try pinging after that, I get the same response as shown above, nothing changes
[/LIST]

[*]ip a
[LIST]
[*]1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
[/LIST]
[/LIST]
[INDENT=3]link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00[/INDENT]
[INDENT=3]indet 127.00.0.1/8 scope host lo[/INDENT]
[INDENT=4]valid_lft forever preferred_lft forever[/INDENT]
[INDENT=3]inet6 ::1/120 scope host[/INDENT]
[INDENT=4]valid_lft forever preferred_lft forever[/INDENT]
[INDENT=2]2: ens33: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000[/INDENT]
[INDENT=3]link/ether 00:0c:29:d8:30:77 brd ff:ff:ff:ff:ff:ff
inet6 fe80::20c:29ff:fed8:3077/64 scope link[/INDENT]
[INDENT=4]valid_lft forever preferred_lft forever[/INDENT]

[LIST]
[*]cat /etc/network/interfaces
[/LIST]
[INDENT]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto ens33
iface ens33 inte dhcp[/INDENT]

[LIST]
[*]I've also tried installing a new ubuntu vm, but whenever I do, the system can't connect to the dhcp server. This makes me wonder if there's an issue with more than just my one vm. But I have a CentOS vm on the same computer that connects to the network just fine, and successfully pings google. The CentOS vm has two network adapters, one static and one using dhcp, both network adapters are connected by sharing with my mac.
[/LIST]


I'm hoping someone can help me reconnect my system to the network or fix whatever is going on. Thanks!!

---

### Post by wildmanne39 on 2018-05-31
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by KillerKelvUK on 2018-06-01
Hey rudy... so ping and apt-get aren't working because they can't resolve the hostnames to IP addresses which means they can't access a DNS server (which is typically supplied by the DHCP process).  The "ip a" command you've used is correct and it should be listing an IP address for your network interface labelled ens33...see my output below for comparison...

```

$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: ens3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 52:54:00:76:fe:b2 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.100/24 brd 192.168.1.255 scope global ens3
       valid_lft forever preferred_lft forever

```

See i use IPv4 addresses so mine is 192.168.1.100 in a /24 subnet...pretty basic stuff, but you don't got one of these :-)

Your config in /etc/network/interfaces is saying to us DHCP on the ens33 interface which should work (provided your network has a DHCP server in it and you've correctly configured vmware) however you have a typo in the syntax here...

> 
[COLOR=#000000]# The primary network interface[/COLOR]
[COLOR=#000000]auto ens33[/COLOR]
[COLOR=#000000]iface ens33 inte dhcp
[/COLOR][COLOR=#000000]

"inte" is the bad boy here, this should be "inet" like you have it for the loopback interface above.  So fix this and restart the networking service or reboot and you should be ready to rock n roll!

Please post back if this does/doesn't solve it for you and please also mark the thread as solved as such.

Best of luck with the course.[/COLOR]

---

### Post by rudy558 on 2018-06-01
Hello, thanks for being willing to help!:D

Yes, sorry, that was a typo on my part while copying the info to the forum. My /etc/network/interfaces does say inet. You raise a good point about how ens33 is missing my IPv4 address, I'm not sure how it was removed or how to add it back. Any thoughts?
Also when I power on the vm, the boot sequence gets hung up with red *** bouncing between brackets and the message "A start job is running for Raise network interfaces (2min 3s / 5min 8s)"

---

### Post by KillerKelvUK on 2018-06-01
Darn it, simple usually wins but not in this case.

Okay lets see so your guest is complaining right from the start it can't raise the network interface so lets first check how you've configured the guest in vmware.  When you say its set to be shared with your mac, can you post a screen shot of this configuration?  I'm not familiar with vmware but is there not a "bridged" networking mode you could select?

---

### Post by rudy558 on 2018-06-01
Ok, I just switched it to bridged, and that seems to have allowed me to ping google, which is AWESOME! \\:D/ Thank you! However, I just trided to install nginx for the assignment and got this as the response:

&#8226; sudo apt-get install ngix
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package nginx

Do you think this is related or a separate issue?

---

### Post by rudy558 on 2018-06-01
Nevermind, I was able to fix that problem by using
sudo apt-get update

Thanks! :cool:

---

### Post by KillerKelvUK on 2018-06-03
:popcorn: glad you got it sorted.

---

