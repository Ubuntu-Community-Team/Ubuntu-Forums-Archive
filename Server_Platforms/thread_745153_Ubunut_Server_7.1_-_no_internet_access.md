---
title: "Ubunut Server 7.1 - no internet access"
date: 2008-04-04
forum: Server Platforms
---

### Post by dnaxx on 2008-04-04
Hello!
I am running Ubuntu Server 7.04. External access to the server works perfect (e.g. http, ftp, SQL, SSH, etc.). But inside the server I cannot connect to the outside e.g. to the internet.
What's going wrong on my machine?

Regards,

---

### Post by ryazkhan on 2008-04-04
Find out your interface for inernet/intranet by typing ***ifconfig***
Bring you interface up > ifup ethx  replace x with your number

---

### Post by dnaxx on 2008-04-04
this returns 
> 
ifup: interface eth0 already configured


As I already stated, I can access the server from outside over the interface but not vice versa.

---

### Post by rickyjones on 2008-04-04
ifconfig eth0

^ That will get you your IP address/subnet.

less /etc/network/interfaces

^ This will tell us how your network interfaces are configured (DHCP or Static).

If it is static then check that file to see if the "gateway" option is configured correctly.

Because clients can talk to your server I am going to assume that the IP address is correct for the network. The fact that you can't go anywhere leads me to believe that the default gateway is not correct on your system.

I hope this helps!

Sincerely,
Richard

---

### Post by dnaxx on 2008-04-04
ifconfig eth0:
> 
eth0      Link encap:Ethernet  HWaddr 00:0C:29:4E:69:DC
          inet addr:192.168.2.13  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe4e:69dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3087 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:273359 (266.9 KiB)  TX bytes:1668368 (1.5 MiB)
          Interrupt:16 Base address:0x2000


less /etc/network/interfaces
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp


Looks ok, doesn't it?

---

### Post by rickyjones on 2008-04-04
Looks like your server is configured to use DHCP to assign addresses and the gateway.

Enter the command "route" and copy/paste the results into thread. Do you know that your default gateway is supposed to be? 

-Richard

---

### Post by dnaxx on 2008-04-04
Yes, the default gateway is 192.168.2.1.

route:
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth1


---

### Post by rickyjones on 2008-04-04
Does this computer have more than one network interface? 

I asked for the ifconfig eth0 command because I assumed only one ethernet connection. According to your routing table it is showing that the default gateway is through eth1.

Try doing "ifconfig" and post the results.

EDIT:

I wanted to throw in my own configuration files so that you might have a better idea on what things should look like.

My server has one network interface.
```

root@vm-webserver:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:29:ED:97:B7
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:feed:97b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1974046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:919003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:440365019 (419.9 MiB)  TX bytes:212689255 (202.8 MiB)
          Interrupt:17 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1072 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:128116 (125.1 KiB)  TX bytes:128116 (125.1 KiB)

root@vm-webserver:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        gateway 192.168.0.1

root@vm-webserver:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         router.zzperfor 0.0.0.0         UG    0      0        0 eth0


```

Thanks,
Richard

---

### Post by dnaxx on 2008-04-04
there is one network interface and a loopback adapter:

> 
eth1      Link encap:Ethernet  HWaddr 00:0C:29:A1:79:7A
          inet addr:192.168.2.13 Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fea1:797a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:17712 (17.2 KiB)  TX bytes:25087 (24.4 KiB)
          Interrupt:16 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



---

### Post by rickyjones on 2008-04-04
Can you ping your default gateway?

---

### Post by dnaxx on 2008-04-04
no. Ping does not work for the gateway nor for other hosts in the network (from within the server). Just pinging 192.168.2.13 works of course.

---

### Post by rickyjones on 2008-04-04
Then lets run through a few other steps.

Is this a dedicated server? If so then we can move it to a static IP address.

1) Configure a static IP address. Please see one of my prior posts for a copy of my /etc/network/interfaces file. Where my file says "auto eth0 inet static" you will want yours to say "auto eth1 inet static". Then use the options below that line (changing your IP/subnet as necessary!).

2) Restart networking. /etc/init.d/networking restart. This will bring your interface down and back up with the new IP address settings.

If you are not able to move it to a static IP at this time due to restrictions on the computer then just try step 2, restart the networking subsystem, and see if that has any effect.

Sincerely,
Richard

---

### Post by dnaxx on 2008-04-04
I tried it this way:
> 
auto eth1
iface eth1 inet static
address 192.168.2.13
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1

No success. Also rebooting of server or restarting of networking has no effect.

Anyway, thanks for your patience :).

---

### Post by rickyjones on 2008-04-04
Still not working? I'm afraid then that I have reached the end of my suggestions from the remote side. I wish you luck in this! If I can think of something else I'll be sure to post it.

Sincerely,
Richard

---

### Post by dnaxx on 2008-04-04
no, it does not work. But I'll post my results (when I get some).

---

