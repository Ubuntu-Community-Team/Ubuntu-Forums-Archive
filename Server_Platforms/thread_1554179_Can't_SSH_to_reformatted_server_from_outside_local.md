---
title: "Can't SSH to reformatted server from outside local network"
date: 2010-08-16
forum: Server Platforms
---

### Post by Zeophlite on 2010-08-16
Okay so I had problems with my Ubuntu Server 10.4, so I reformatted and reinstalled (I only choose OpenSSH from the install menu), then after it rebooted I installed apache.

So I can access the machine via web, ssh and scp from within my local network, but strangely outside my network I can access it from web, but not ssh or scp.  Nothing has changed on my router.

I'm guessing that I forgot to change some setting, but I'm not sure which one.

---

### Post by LightningCrash on 2010-08-16
Sounds like the default route is messed up

```
netstat -rn
```

Make sure you see your router's IP in there

---

### Post by Iowan on 2010-08-16
> **Zeophlite said:**
> I'm guessing that I forgot to change some setting, but I'm not sure which one. Are you using the standard port? If it's working locally, and the router is forwarding to the correct port...

---

### Post by CharlesA on 2010-08-16
Make sure that the ip hasn't changed.

Just a thought.

---

### Post by Zeophlite on 2010-08-17
> **LightningCrash said:**
> Sounds like the default route is messed up

```
netstat -rn
```

Make sure you see your router's IP in there


I'll run that tonight and post the output, but is there any configuration files I should inspect?  I can access the server, but I have with me a full copy of the entire filesystem (before and after).  What should I compare?



I guess its using the standard port (it was a standard install).  The router hasn't changed, so port forwarding is working (web works after all).  And the server's got the correct ip address (its mac address hasn't changed, and the router assigns based on that), and the external ip address hasn't changed (its static from my IP).  Anyway, as I said before, web works remotely, so that can't be it.

---

### Post by Zeophlite on 2010-08-17
I ran the command you asked.
```

**daniel@Mustrum:~$ netstat -rn**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
**daniel@Mustrum:~$ cat /etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

I remembered that I changed the /etc/network/interfaces on my old setup (preformat), and so I changed the file to below, restarted, but its had no effect on netstat.
```

**daniel@Mustrum:~$ netstat -rn**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
**daniel@Mustrum:~$ cat /etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 
# The loopback network interface
auto lo
iface lo inet loopback
 
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.73
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

---

### Post by LightningCrash on 2010-08-17
your server looks fine... are you sure the port forwarding is set up properly on your router?

---

### Post by Zeophlite on 2010-08-17
It definitely is.  Nothing has changed on it - worked before and nothing changed with it.  I've also checked all its settings, and they are the same as before (as in when SSH was working).

---

### Post by CharlesA on 2010-08-17
You said that you changed /etc/network/interfaces before, so make sure you have port forwarding set up correctly.

---

### Post by Zeophlite on 2010-08-17
You misunderstand.  The server is a separate piece of hardware to the router.  So port forwarding (at least on the router) is correct - again, it definitely is because I have checked this.  If there's some setting on the server to configure port forwarding, please tell me.

---

### Post by CharlesA on 2010-08-17
Please postthe output of **netstat -l**

Do you have sshd listening on a non-standard port?

---

### Post by Linxwiz on 2010-08-17
Is your firewall not preventing you from connecting? check iptables -L -v

---

### Post by arrrghhh on 2010-08-17
> **Zeophlite said:**
> You misunderstand.  The server is a separate piece of hardware to the router.  So port forwarding (at least on the router) is correct - again, it definitely is because I have checked this.  If there's some setting on the server to configure port forwarding, please tell me.

By default, Ubuntu does not ship with a firewall enabled/configured.  UFW is the front-end Ubuntu provides for iptables - if you haven't enabled it, then you don't have to worry about the server blocking the traffic (although I would recommend turning it on & configuring it, so that way you're only opening the ports you want open)

With that said, it looks like you switched between DHCP and a static IP there.  Perhaps this has been addressed (I didn't notice, I apologize if it has) but are you using the exact same IP as you were previously?  Most routers forward ports based on the local IP address, one of the main reasons I recommend using a static IP if you're running any services port forwarded thru your router.

Since it is working locally, how are you trying it on the WAN?  Are you going directly to the WAN IP, are you using something like dyndns.org to give yourself a domain name...?  I know there has been problems when people try to connect to their external domain name even when they're still on their own LAN.  The true test of WAN connectivity is to use a separate ISP - for example, I tether the connection on my Sprint phone when I want to test changes made to my server which is on a Comcast connection.

---

### Post by Zeophlite on 2010-08-19
```

daniel@Mustrum:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:www                   *:*                     LISTEN
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     3606     /var/run/apache2/cgisock.794
unix  2      [ ACC ]     STREAM     LISTENING     2696     @/com/ubuntu/upstart

```

I'll post the iptables command tonight

---

### Post by Zeophlite on 2010-08-19
> **arrrghhh said:**
> Since it is working locally, how are you trying it on the WAN?  Are you going directly to the WAN IP, are you using something like dyndns.org to give yourself a domain name...?  I know there has been problems when people try to connect to their external domain name even when they're still on their own LAN.  The true test of WAN connectivity is to use a separate ISP - for example, I tether the connection on my Sprint phone when I want to test changes made to my server which is on a Comcast connection.

Internally, I used its internal IP address, and externally I used my home's external IP address (same as prereformat) from a different ISP.

---

### Post by v1ad on 2010-08-19
this is what i think happened. ports for a specific ip address where set previous to the reinstall. it all worked great then. reinstalled & ip changed. therefore resulting in having the ports opened for the wrong ip address.

ip port 22 is open even to the local network, there is only the router in conflict. make sure that you are forwarding port 22 to only 1 ip address....

make sure that 192.168.1.73 is same as in router settings.

---

### Post by CharlesA on 2010-08-19
Hrm, need the port number, try this:

```
netstat -ln
```

---

### Post by Zeophlite on 2010-08-20
```

**daniel@Mustrum:~$ sudo iptables -L -v**
[sudo] password for daniel:
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
 
Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
 
Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
**daniel@Mustrum:~$ netstat -ln**
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     3606     /var/run/apache2/cgisock.794
unix  2      [ ACC ]     STREAM     LISTENING     2696     @/com/ubuntu/upstart
**daniel@Mustrum:~$**

```

---

### Post by CharlesA on 2010-08-20
Well SSH is listening on the correct port and there aren't any firewall rules in place.

Double check the ip address on the box and make sure that it matches the one you set for port forwarding.

---

### Post by Zeophlite on 2010-08-20
How do I find my IP address?

---

### Post by arrrghhh on 2010-08-20
> **Zeophlite said:**
> How do I find my IP address?

For your local (LAN) IP do an ifconfig from the terminal.

For your internet (WAN) IP there's a couple of ways.  Your router usually will have it listed, or you can go to a website like [http://whatismyip.com](http://whatismyip.com)

---

### Post by v1ad on 2010-08-20
u only need your local ip address. 

ifconfig and under eth0 u will see your ip. look at my upper post and if i remember correctly you already provided us your local ip.

open up a web browser and type in: 192.168.1.1
and it will pop up a dialog for you to log in. log in (prob set on default username & pass -google if you don't know default)

look through it till you find port forwarding and make sure there is only 1 ip address set for port 22. and so it would match your current local ip of the server.

---

### Post by Zeophlite on 2010-08-20
> **Zeophlite said:**
> So I can access the machine via web, ssh and scp from within my local network, but strangely outside my network I can access it from web, but not ssh or scp.  Nothing has changed on my router.

I checked my routers settings and its port forwarding is correct.
I access both web and ssh (unsuccessfully) from the same external IP address externally, and web and ssh (successfully) from the same internal IP address internally.

---

### Post by v1ad on 2010-08-20
still feel like its a router issue .... try it directly from modem and see if it is actually the issue.

---

### Post by Zeophlite on 2010-08-21
What do you mean?

---

### Post by arrrghhh on 2010-08-21
> **Zeophlite said:**
> What do you mean?

Take the router out of the equation, and plug your server's ethernet cable directly into the cable modem, or whatever your edge device is.

I'm assuming since this worked before you're on the same ISP...?  It is possible that your ISP is blocking the traffic, but since it worked before I think we're all assuming that's not the case.

---

### Post by Zeophlite on 2010-08-21
The router is the modem, and its the same ISP.

---

### Post by CharlesA on 2010-08-21
Move SSH to a different port and change the port forwarding rules then try to connect.

That would rule out the ISP blocking port 22.

---

### Post by arrrghhh on 2010-08-22
> **Zeophlite said:**
> The router is the modem, and its the same ISP.

That's unfortunate.  It also almost certainly points to this device not being configured correctly, or your ISP is just blocking the traffic.

So try changing to a port above 1024 - hopefully your ISP won't block that.  Just don't do the popular ones like 8080, 8443, etc.

---

### Post by kevinthecomputerguy on 2010-08-22
Zeophlite-

Your work computer could have cached the old ssh keys from your first server build. Then when you rebuilt the server, you got a new set of ssh keys. If you dont know how to delete your old ssh keys from your work computer, just try it from a buddies computer at your work. If thats the first time your buddy has ssh into your box, he wont have the old key.

If that works, let us know, and we can tell you how to delete the old ssh key on your work computer.

---

### Post by v1ad on 2010-08-22
or log into your router-modem and put that server on dmz mode that way it bypasses the modem firefall.

---

