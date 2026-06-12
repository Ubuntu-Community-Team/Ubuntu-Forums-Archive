---
title: "LTSP Server Issue - Client doesn't boot"
date: 2010-09-17
forum: Server Platforms
---

### Post by guiclaw on 2010-09-17
Hi,

I've recently discovered LTSP and I've been trying to get it set up and working using Ubuntu 10.04. I've followed the guide on the Wiki, and I can see in the syslog that the client successfully gets an IP, and the client starts to load files, and after it's finished loading it just sits there doing nothing.

I saw a post somewhere saying that 10.04 doesn't work with LTSP straight out of the box like 9.10 did - so I've tried 9.10 as the server machine to no avail.

I'm running 64bit Ubuntu on the server, with ltsp-build-client --arch=i386 and it successfully creates the images so there's amd64 and i386 in /opt/ltsp.

The client machine I'm trying to boot is a Dell Optiplex GX280 with 1GB RAM using the built-in Intel network adapter and PXE. I've also tried booting an Acer Revo which also shows the same issue.

The server is a Rackable Systems dual Operon machine with 4GB ram and dual gigabit interfaces.

Does anyone know why this would be happening? There's no errors of any kind in the syslog and I'm at a bit of a loss as to where to debug this further. The only info in the log of the LTSP boot is:

```

Sep 17 13:59:38 ubuntultsp dhcpd: DHCPDISCOVER from 00:0d:56:8d:13:2b via eth1
Sep 17 13:59:39 ubuntultsp dhcpd: DHCPOFFER on 192.168.0.20 to 00:0d:56:8d:13:2b via eth1
Sep 17 13:59:39 ubuntultsp dhcpd: DHCPREQUEST for 192.168.0.20 (192.168.0.1) from 00:0d:56:8d:13:2b via eth1
Sep 17 13:59:39 ubuntultsp dhcpd: DHCPACK on 192.168.0.20 to 00:0d:56:8d:13:2b via eth1
Sep 17 13:59:41 ubuntultsp nbdrootd[1823]: connect from 192.168.0.20 (192.168.0.20)
Sep 17 13:59:41 ubuntultsp nbd_server[1824]: connect from 192.168.0.20, assigned file is /opt/ltsp/images/i386.img
Sep 17 13:59:41 ubuntultsp nbd_server[1824]: Size of exported file/device is 215052288

```

Thanks!

---

### Post by lykwydchykyn on 2010-09-17
Are there any errors in your auth log (/var/log/auth.log)?

---

### Post by guiclaw on 2010-09-17
Unfortunately nothing at all - it only shows my own SSH logins and sudos, nothing to do with LTSP or any failures.

Edit:
Just left it for ages and it got somewhere further - it showed the Ubuntu logo and then went to text-mode saying something to do with things already mounted - and now it's gone to a blank screen now. There's no network activity and it's not showing any signs of life now in this blank screen. Still no errors in the logs either.

Looked like it took more than 5 minutes for it to even show the Ubuntu logo - is this normal for a LTSP boot? It's only running over a 100Mbps connection as that's the speed of the Dells NIC - I have a D-Link low profile NIC but it doesn't have a PXE chip on it so I can't easily test this.

The error it showed:
```

udhcpc[265]: udhcpc (v0.9.9-pre) started
udhcpc[265]: Sending discover...
udhcpc[265]: Sending discover...
udhcpc[265]: Sending select fo 192.168.0.20...
udhcpc[265]: Lease of 192.168.0.20 obtained, lease time 43200

mount: according to mtab, aufs is already mounted on /

mountall: mount / [330] temrinated with status 1
mount: according to mtab, none is already mounted on /proc

mountall: mount /proc [330] temrinated with status 1
mount: according to mtab, none is already mounted on /sys

mountall: mount /sys [330] temrinated with status 1
mount: according to mtab, none is already mounted on /dev

mountall: mount /dev [330] temrinated with status 1
mount: according to mtab, none is already mounted on /rofs

mountall: mount /rofs [330] temrinated with status 1
mount: according to mtab, none is already mounted on /cow

mountall: mount /cow [330] temrinated with status 1

```

Edit 2:
It's now showing "Setting up LTSP client..." and "Starting LTSP client....." but it seems to be taking much longer than expected - and the interface is only showing about 180Kbps throughput.

Edit 3:
Tried it on a C2D - much newer hardware and it booted to the login screen almost instantly, and lets me login - it hangs whilst verifying password with a terminal in the upper left hand quarter of the screen and I see a successful auth in auth.log but then it hangs, so I'm wondering if it's randomly incompatible with a Pentium 4?

---

### Post by lykwydchykyn on 2010-09-17
It should boot much faster than that on the GX280.  I've got a system running on 200MHz thin clients, and while it's painfully (and often problematically) slow, it gets to the login screen in about 3 minutes.  I've used it with P3 500MHz laptops and it boots up in less than a minute.

I haven't tested a Gx280 as a client (though ironically I ran an LTSP server on one for about 3 years), but I wouldn't be surprised if it just had some basic incompatibility issue or hardware failure.  We buy all dell optiplexes where I work, and the 280 has been the flakiest optiplex model we've ever bought.

---

### Post by tlink123 on 2010-09-26
I have setup up an LTSP environment where by my server is HP DL380 G6 and my clients are DELL Optiplex G280. I am facing similiar problem where the client pc's hang some time after successful log in. i have tried almost everything and non of it help.

---

