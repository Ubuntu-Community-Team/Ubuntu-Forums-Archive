---
title: "can't see internet from server"
date: 2012-10-05
forum: Server Platforms
---

### Post by broecher on 2012-10-05
I have a computer set up and working as a headless samba server, but it has no internet access. I would like to make it an ftp server but i can't even access the software repository....

Here are some of my settings and things. Any ideas what I should do?

Its ubuntu server 9.04. 

My ifconfig output:
> me@ubuntuServer:/etc/network$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:05:5d:50:*
          inet addr:192.168.0.169  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::205:*:acc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:253819 (253.8 KB)  TX bytes:142009 (142.0 KB)
          Interrupt:16 Base address:0xdc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1752 (1.7 KB)  TX bytes:1752 (1.7 KB)

my interfaces file:
>   GNU nano 2.0.9              File: interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.169
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1


My google ping attempt:
> me@ubuntuServer:/etc/network$ ping -c3 64.233.169.103
PING 64.233.169.103 (64.233.169.103) 56(84) bytes of data.

--- 64.233.169.103 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2004ms

and my router numbers:
> WAN

Connection Type : DHCP Client
Cable Status : Connected
Network Status : Established
Connection Up Time : 27 Days, 12:19:11
    
MAC Address : 00:E0:18****
IP Address : 208.******.0
Subnet Mask : 255.255.254.0
Default Gateway : 208.******.1
Primary DNS Server : 24.220.0.10
Secondary DNS Server : 24.220.0.11

LAN

MAC Address : 00:1E:58:*****
IP Address : 192.168.0.1
Subnet Mask : 255.255.255.0
DHCP Server : Enabled

I changed the range of DCHP to not includ my static IP for the server of 192.168.0.169  :

> DHCP SERVER SETTINGS
Use this section to configure the built-in DHCP Server to assign IP addresses to the computers on your network.


Enable DHCP Server: 
DHCP IP Address Range: 192.168.0.100 to 192.168.0.160 
DHCP Lease Time:  1440 (minutes)
Always broadcast:  (compatibility for some DHCP Clients)

---

### Post by volkswagner on 2012-10-06
Are you sure the server has no internet access?

What do you get when you run the following:

```
host google.com
```
or
```
wget http://www.google.com/index.html
```


Perhaps you can't connect to the repository because 9.04 has reached end of life in Oct 2010?

---

### Post by broecher on 2012-10-06
I didn't realize the repositories get closed - I thought they would just not be updated... That could be a problem I guess, 12.04 wouldn't install on this computer.

> me@ubuntuServer:~$ host google.com
;; connection timed out; no servers could be reached

me@ubuntuServer:~$ wget [http://www.google.com/index.html](http://www.google.com/index.html)
--2012-10-05 21:44:04--  [http://www.google.com/index.html](http://www.google.com/index.html)
Resolving [www.google.com](www.google.com)... failed: Name or service not known.
wget: unable to resolve host address `[www.google.com](www.google.com)'

---

### Post by broecher on 2012-10-06
If I could get the internet working, maybe what is described in this post is still possible.

[http://superuser.com/questions/339537/where-can-i-get-theold-repositories-for-ubuntu-9-04-jaunty](http://superuser.com/questions/339537/where-can-i-get-theold-repositories-for-ubuntu-9-04-jaunty)

---

### Post by darkod on 2012-10-06
To your interfaces file add also dns servers like:
dns-nameservers 192.168.0.1 8.8.8.8

When you say 12.04 wouldn't install, have you tried? If you are running the server version, I wouldn't say it uses that much more resources.

On the other hand, if you are using the desktop version as a server, yes, the 12.04 might not install on machines that can run 9.04.

But in any case, 9.04 is not supported any more long time ago and you need to start thinking about other options I guess.

PS. The ping to an IP doesn't work, so it is not only a question of dns. Can you ping the router at 192.168.0.1? That's the first thing to see, if it has connection with the router at all. If you can't ping the router, double check the connections.

---

### Post by broecher on 2012-10-06
Yes it will ping the router. I am accessing it from putty on another computer right now.

I tried to install 12.04 two times. It acted like it was working but then after it said to remove the cd, it would not boot. If I remember correctly, it there was no bios page or anything, escape and F-keys did nothing, just a black screen.

---

### Post by darkod on 2012-10-06
Well, your network settings look correct.

Have you activated any firewall on the server maybe?

On another note, BIOS and getting into it have nothing to do with the OS. It's weird if you could not get into BIOS regardless which OS you want to install.

Sounds like maybe only the bootloader didn't install, or if you have multiple disks maybe it installed on one disk and you are booting from another disk.

---

### Post by broecher on 2012-10-06
Thanks for the advice. I may try to re-install 12.04 again and see if I can figure out what the problem with it was.

I just disabled ufw completely and it still cannot reach the internet.

---

### Post by darkod on 2012-10-06
If you tried to play with ufw too much, you might have caused this yourself. But ssh access seems to be working fine... Strange...

In any case, ufw is sometimes weird, you might want to flush the iptables rules too, something like:
sudo iptables -F

If you do a new install, try the internet first after setting up the static IP. See if it works.

Only then start configuring firewalls and stuff. At least you will know if it worked "out of the box".

---

### Post by kennethconn on 2012-10-06
```
network 192.168.0.0
broadcast 192.168.0.255
```
My interfaces file does not have these entries (and only has the router as it's dns-naneservers).

Have you restarted networking on server?
Restarting router?

Can't really think of much more.

---

### Post by darkod on 2012-10-06
> **kennethconn said:**
> ```
network 192.168.0.0
broadcast 192.168.0.255
```
My interfaces file does not have these entries (and only has the router as it's dns-naneservers).

Have you restarted networking on server?
Restarting router?

Can't really think of much more.

If you set a static IP during installation, it adds those lines in /etc/network/interfaces.

If you don't catch the Cancel button during installation when it configures the network, and configure a static IP yourself later, usually nobody enters them. It works without them just fine, it works with them too.

The issue is really weird, it all looks correct, unless it was something with the firewall.

---

### Post by broecher on 2012-10-06
i'm focusing on the 12.04 installation now so i started another thread. [_http://ubuntuforums.org/showthread.php?p=12281648#post12281648_]("http://ubuntuforums.org/showthread.php?p=12281648#post12281648")

thanks for all the suggestions!!

---

### Post by broecher on 2012-10-07
i installed 10.04 and let it automatically setup networking and it worked, i had access to the internet.

decided to try upgrading to 12.04, and it looked like it worked but after the reboot the screen goes black after bios still.

BUT this time i went to another computer and just tried to log on to it and IT WORKED!!

I don't know why but 12.04 will not send a signal to the monitor...

---

