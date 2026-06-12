---
title: "[SOLVED] Making a bridge with static IP's for virtualbox in /etc/network/interfaces"
date: 2008-02-06
forum: Virtualisation
---

### Post by Levander on 2008-02-06
I followed this HOWTO which does most of what I want:

[http://www.virtualbox.org/discussion/1/126](http://www.virtualbox.org/discussion/1/126)

It creates a static IP for my XP guest running under virtualbox.  But, I also want a static IP for the host.  The HOWTO says to have eth0 configured in the /etc/network/interfaces file as:

```

auto eth0

iface eth0 inet manual 

```

However, when I do that, there's no IP listed for eth0 in the output if ifconfig after reboot.

So, I tried guessing what the config for eth0 in /etc/network/interfaces should look like.  I came up with this:

```

iface eth0 inet static
      address 192.168.0.63
      netmask 255.255.255.0
      gateway 192.168.0.1
auto eth0

```

It kind of works.  This is the output for eth0 from the "ip addr" command after reboot:

```

2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:1d:7d:a2:77:6b brd ff:ff:ff:ff:ff:ff
    inet6 fe80::21d:7dff:fea2:776b/64 scope link 
       valid_lft forever preferred_lft forever

```

There's no IP address for eth0.

But, if after booting I run an ifup and ifdown command like this:

```

levander@louis:~$ sudo ifdown eth0
SIOCDELRT: No such process  # this just comes up when I run this command, no idea what it means
levander@louis:~$ sudo ifup eth0

```

Then, this is the output for eth0 from 'ip addr':

```

2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:1d:7d:a2:77:6b brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.63/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::21d:7dff:fea2:776b/64 scope link 
       valid_lft forever preferred_lft forever

```

See?  There's now my wanted static IP address for eth0.

Anybody know how I can get /etc/network/interfaces configured so I don't have to run the ifup and ifdown commands after every reboot to get my static IP?

---

### Post by Levander on 2008-02-07
Well, a little disappointed at no responses.

But, I figured something out last night.  It seems like the IP address of the bridge is the IP address of the machine.  eth0 is just attached to the bridge somehow...  

So, I think, the static IP of the bridge is the static IP of the machine....

---

### Post by Het Irv on 2008-02-07
Yes there is a IP address for eth0
the line "inet6" is your IPv6 address which is the same in both

IPv6 looks very different than IPv4 because it is in Hexidecimal.  I haven't researched it much, guess it's time to learn it.
You are close enough on how a bridge works.  Basically it forwards every thing that hits it in either direction.  Almost like having an external wireless card.

---

### Post by Levander on 2008-02-07
[QUOTE=Het]You are close enough on how a bridge works.  Basically it forwards every thing that hits it in either direction.  Almost like having an external wireless card.[/QUOTE]

So, how does the bridge decide which direction to send incoming packets to?  Like if someone wants to ssh into my linux host, how does the bridge know that it should send the connection to the linux host and not the windows guest?

---

### Post by Het Irv on 2008-02-08
There is another virtual bridge on your computer between the VM and your computer that deciedes which packets are for the VM.

---

### Post by Levander on 2008-02-08
Okay, but how does it decide?  Is there a configuration file somewhere?

---

### Post by Het Irv on 2008-02-08
I guess...but I don't know where it is.  Why do you need to use Static Host IP's?

---

### Post by Levander on 2008-02-09
Apparently the IP of the bridge is the external IP of the host.  And then your guest OS configures it's own IP however it wants via dhcp or static or whatever.  The external IP of the guest is this IP that the guest OS has configured.

I need static IP's because I run servers that I forward ports to from my router.

---

### Post by Levander on 2008-02-09
So basically, you don't need to configure an IP address for eth0 on the host.  Your external IP is thoe IP of the bridge.

You just don't need to do what I did in the second code snippet in the original post.

The HOWTO I linked to does give you a static external IP.

---

### Post by karyonix on 2008-02-10
You are right.
Don't assign an IP to eth0. Assign it to the bridge instead. It'll be the machine's IP as seen from all machines connected to bridged interfaces.

---

