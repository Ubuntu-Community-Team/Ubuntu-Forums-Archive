---
title: "Gateway Setup in Lab Environment"
date: 2017-04-05
forum: Virtualisation
---

### Post by blogmore on 2017-04-05
Hello everyone,

I am posting here in the Ubuntu forums, because I believe the community here would be best able to help.


I am trying to run a small lab, with various components thrown in.
I believe the combination of components is what is making this difficult.


Yet, in short, I would like to accomplish three things: 
- I would like to run FreeIPA on a Fedora server, to manage Xubuntu clients.
- I also want to do this "inside" VirtualBox, while all the virtual machines (VMs) are running on a Xubuntu host.
- I would like to use an Ubuntu 16.04 server to act as a gateway/firewall and DHCP server to this internal network


[I attach a basic diagram]("http://imgur.com/a/K8r7K") to this post showing the "layout".


There are two problems that are "hanging me up" at the moment.
First, the Fedora server (freeIPA manager) is unable to "ping 8.8.8.8"  UNLESS I first ping that Fedora VM from the Ubuntu gateway/DHCP server.


So if I go into the Fedora VM, and:
ping 8.8.8.8   ---- fail


If I go into the Ubuntu server (gateway/DHCP server), and ping the Fedora VM
ping 192.168.89.10  ---- success and it works


Then, on the Fedora VM:
ping 8.8.8.8 ---- success and it works




The second problem is that the Fedora VM cannot  "ping [google.com]("http://google.com/")"
To setup DNS, do I set them up in the Ubuntu (via bind9)?
Or can I use 8.8.8.8 as DNS?


So, first problem to solve:
How can the Fedora VM ping 8.8.8.8 "from zero" (without needed the gateway to ping it first)?


Second problem:
What should I do about DNS?

[IMG]http://imgur.com/a/K8r7K[/IMG]

Everything inside the Ubuntu server gateway (fw-ubuntu-01 in the network diagram):
Here are the "iptables rules"  I have placed inside...

This is inside /etc/rc.local
```
/sbin/iptables -t nat -A POSTROUTING -o enp0s3 -j MASQUERADE
/sbin/iptables -A INPUT -i enp0s8 -j ACCEPT
/sbin/iptables -A INPUT -i enp0s3 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A OUTPUT -j ACCEPT
```

Also, inside /etc/sysctl.conf, I have un-commented the line:
```
net.ipv4.ip_forward=1
```


I have also installed isc-dhcp-server

---

### Post by howefield on 2017-04-05
Thread moved to the "*Virtualisation*" forum.

---

### Post by blogmore on 2017-04-05
Finally was able to "embed" the image for the network diagram.
[IMG]http://i.imgur.com/tAGcpKw.jpg[/IMG]

---

### Post by blogmore on 2017-04-06
If I run
```
arp -a
```
In the "internal" Fedora VM (192.168.89.10) I get:
```
[blogmore@ipa-server-01 ~]$ arp -a
gateway (192.168.89.1) at 08:00:27:d8:00:70 [ether] on enp0s3
? (192.168.89.2) at <incomplete> on enp0s3
```

Yet now I can ping 8.8.8.8 from within the Fedora VM fine.
Apparently, it takes a couple of minutes if I reboot the Ubuntu Gateway/DHCP machine.

Yet I still cannot ping google.com from withing the Fedora VM.

==== HOLD THE PRESS ====

Now I can in fact ping google.com and it works!

I think it is once again:
[I]Apparently, it takes a couple of minutes if I reboot the Ubuntu Gateway/DHCP machine.
[/I]
I have taken note of this... lets see!

---

### Post by blogmore on 2017-04-06
Hello again,
I have a question.

Now that the Fedora VM that is "behind" the Ubuntu gateway is able to ping the internet...
I install iftop in the Ubuntu gateway.

I then ran the monitoring on the NIC facing the "inside" network (the one connected to the Fedora VM - 192.168.89.0/24).
```
sudo iftop -i enp0s8
```

I then watched the traffic.
I can see the "ping google.com" from the Fedora VM, when she connects to 1e100.net (google).
Yet why is she connecting/pinging mail.coldnorthadmin.com?
What about kashra.pictures?

Any ideas?
I attach screenshot below.
[IMG]https://i.imgur.com/heF3TIA.png[/IMG]

---

### Post by blogmore on 2017-04-06
Ok, I just asked over in the irc #fedora, and the guys there quickly pointed out that kashra.pictures is one of the servers in the Fedora ntp pools.

So it's all good.
:)

---

### Post by blogmore on 2017-04-11
Now I am running into a slightly different problem:
Same network setup/diagram as above...
Yet if I try to  ping google.com    it doesn't resolve.
It fails with ping: unknown host google.com

The link I am trying [to use as a guide is the following]("https://lani78.com/2012/07/22/setting-up-a-dns-for-the-local-network-on-the-ubuntu-12-04-precise-pangolin-server/").

---

### Post by blogmore on 2017-04-12
I am now wondering if it would be a good idea to create three separate virtual machines.  
- gateway (internal/external network)
- dhcp
- dns

Any opinions or suggestions?

---

### Post by blogmore on 2017-04-13
Well, the issue for DNS has been solved. 
[Here is the thread on the Networking section of the forums]("https://ubuntuforums.org/showthread.php?t=2358356").

I will continue the documentation process of this small lab here.

---

