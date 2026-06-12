---
title: "Slow download speeds on Ubuntu 10.10"
date: 2011-04-17
forum: Server Platforms
---

### Post by jinx55 on 2011-04-17
Hi all,

I've installed Ubuntu server 10.10 64bit onto my Intel Centrino Duo laptop to experiment with setting up some dedicated game servers and gain some experience with linux.

All is fine except I'm having trouble with my download speeds on the Ubuntu server, this will not exceed 150Kbytes/s so I decided to test this using Zen internet's 100MB test file. ([http://fuller.zen.co.uk/test/](http://fuller.zen.co.uk/test/))

Using my Windows 7 64bit machine I can download this file at 6000Kbytes/s so it downloads in a matter of seconds. Yet when using my Ubuntu server to download the same file from exactly the same location I'm not getting anymore than 150kbps.

I'm doing this using
 "wget http://fuller.zen.co.uk/test/100MB_nonzero.bin"

Both Ubuntu and the windows machine are connected to the same network through the same Router and there is no problem transferring large files across the LAN between the Win7 machine and Ubuntu.

I consider myself a begineer when it comes to Linux and would appreciate any suggestions.

Regards,

jinx55

---

### Post by elico on 2011-04-17
the first question is: what is your internet line speed?
second: if you can try download the file using aria2 (aria2c) just to test.(it's an advanced download software that can be used almost the same as wget).
> aria2c "http..."
an 
> ifconfig 
command output can help a bit

---

### Post by jinx55 on 2011-04-17
1) I have a 50Mbit cable connection from Virgin Media.

2) The download speeds are slow whether I'm using FTP, wget, apt-get install or  downloading server files through hldsupdatetool / steam.

The downloads seem start at a max of 150KB/s and slow to a complete halt over a few minutes.

```
ifconfig
eth0        Link encap:Ethernet  HWaddr 00:16:36:be:67:b4
               inet addr: 192.168.0.104  Bcast: 129.168.0.255  Mask: 255.255.255.0
               inet6 addr: fe80::216:36ff:febe:67b4/64 Scope:Link
               UP BROADCAST RUNNING MULTICAST  MTU: 1500  METRIC: 1
               RX packets:351143 errors:5118 dropped:5120 overruns:5118 frame:0
               TX packets:200111 errors:0 dropped:0 overruns:0 carrier:0
               collisions:0 txqueuelen:1000
               RX bytes:517195768 (517.1 MB)   TX bytes:13368124 (13.3 MB)
               Interrupt:17 Base address:0x2000

lo            Link encap:Local Loopback
               inet addr:127.0.0.1 Mask:255.0.0.0
               inet6 addr: ::1/128 Scope:Host
               UP LOOPBACK RUNNING  MTU:16436  METRIC: 1
               RX packets:1517 errors:0 dropped:0 overruns:0 frame:0
               TX packets:1517 errors:0 dropped:0 overruns:0 carrier:0 
               collisions:0 txqueuelen:0
               RX bytes:251049 (251.0 KB)   TX bytes:251049 (251.0 KB)

virbr0       Link encap:Ethernet   HWaddr b2:23:2c:cc:83:f2
                inet addr:192.168.122.1  Bcast:192.168.122.255 Mask: 255.255.255.0
                inet6 addr: fe80::b023:2cff:fecc:83f2/64 Scope:Link
                UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
                RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 txqueuelen:0
                RX bytes:0 (0.0 B)   TX bytes:22683 (22.6 KB)
```

---

### Post by jinx55 on 2011-04-17
Just installed and tried Aria2c

It starts downloading the file at 2.7MiBs which quickly drops down to 200KiBs then after about 10seconds it stops completely at 0B.

Windows downloads this file at a consistant 6MB/s

---

### Post by jinx55 on 2011-04-17
Just tried a fresh install using Ubuntu Server 10.04 32bit version, no apps or extras installed. 

Still getting exactly the same problem..

---

### Post by jinx55 on 2011-04-18
Right, I've finally managed to resolve the issue :)

I was so focused on trying to resolve the issue within Ubuntu, that it didn't even cross my mind that it could be the laptops NIC.. until I left it for the night and got some sleep.

So this morning, I removed the Ethernet cable and setup Wi-Fi, suddenly my downloads are hitting 3-4Mb/s. I tried the same Ethernet cable on another laptop, no issues at all, so this leaves the NIC, though I haven't yet figured out if it's a hardware fault or driver issue.

---

### Post by Sirkyuubi on 2011-04-18
You could be getting throttled through your isp. Wired, and wireless connections would show different mac addresses. Try downloading from a fast SFTP server.

---

### Post by jinx55 on 2011-04-18
> **Sirkyuubi said:**
> You could be getting throttled through your isp. Wired, and wireless connections would show different mac addresses. Try downloading from a fast SFTP server.

If it was my ISP throttling me, I would experience the same problem on my Windows 7 machine that is on the same network.

Not really sure what you're getting at with the different MAC addreses comment, the Wired and Wireless adapters are seperate devices so they will have unique MAC addresses.

Thanks for taking the time to comment, though I doubt you even bothered reading my post.

---

### Post by M1ck3y on 2011-04-28
I always have this problem with Ubuntu. I'm not sure what it is but I have a dual booted machine and on the Windows end I consistently get 1MB+ per second while on Ubuntu I'm lucky to get 20kB+. It's one of the main reasons I don't use Ubuntu much. I'm sure it's not happening to everyone but doing a quick Google search reveals a bunch of people having this problem.

---

### Post by rubylaser on 2011-04-28
what is your hardware? Just use lspci to take a look.
```
zack@fileserver:~$ lspci | grep Ethernet
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)
05:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 11)

```

---

