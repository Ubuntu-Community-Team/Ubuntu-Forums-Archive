---
title: "Server keeps changing IP address"
date: 2011-09-22
forum: Server Platforms
---

### Post by arbulus on 2011-09-22
I have an Ubuntu 11.04 server with a static IP address set. But it seems that it will randomly stop using the static address and get one from DHCP. If I restart the networking service, it reverts to the correct static address. But I don't understand why it keeps looking for a DHCP address. 

Thanks for your help!

---

### Post by volkswagner on 2011-09-22
Please post output of the following.

```
cat /etc/network/interfaces
```

```
ifconfig
```

---

### Post by arbulus on 2011-09-22
/etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address	10.0.1.202
	netmask	255.255.255.0
	gateway 10.0.1.1
```

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:0f:3d:f3:28:f5  
          inet addr:10.0.1.202  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:3dff:fef3:28f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1541722 (1.5 MB)  TX bytes:255134 (255.1 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:315080 (315.0 KB)  TX bytes:315080 (315.0 KB)

```

---

### Post by papibe on 2011-09-22
What are the symptoms of the IP change?

Are other machines trying to access the server with other IP? or

The server itself change its IP (ifconfg) ?

Regards.

---

### Post by arbulus on 2011-09-23
It's a samba server.  My desktop is set to mount a couple of shares from the server at boot via the static address I gave the server. When I restarted my desktop it was unable to reconnect to the shares. When I looked at the server I saw that the ip address had changed.  This has happened a couple of times over the last few days.

---

### Post by papibe on 2011-09-23
Could you post the result of these commands?

```
$ grep -i dhc /var/log/syslog

$ ps aux | grep dhc

```
This is what I'm going here. I'm guessing that you did not restart your server, then dhclient is still running. Those 2 commands should be evidence of that.

If so, you can either restart your machine, or kill the process dhclient.

I hope this helps,
Regards.

---

### Post by arbulus on 2011-09-23
It looks like you may be right.

grep -i dhc /var/log/syslog:

```
Sep 23 06:25:13 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 06:26:21 fileserver dhclient: last message repeated 4 times
Sep 23 06:27:36 fileserver dhclient: last message repeated 5 times
Sep 23 06:28:36 fileserver dhclient: last message repeated 4 times
Sep 23 06:29:36 fileserver dhclient: last message repeated 5 times
Sep 23 06:30:36 fileserver dhclient: last message repeated 4 times
Sep 23 06:31:36 fileserver dhclient: last message repeated 3 times
Sep 23 06:32:36 fileserver dhclient: last message repeated 6 times
Sep 23 06:33:36 fileserver dhclient: last message repeated 4 times
Sep 23 06:34:36 fileserver dhclient: last message repeated 4 times
Sep 23 06:35:36 fileserver dhclient: last message repeated 3 times
Sep 23 06:36:36 fileserver dhclient: last message repeated 4 times
Sep 23 06:37:36 fileserver dhclient: last message repeated 5 times
Sep 23 06:38:36 fileserver dhclient: last message repeated 5 times
Sep 23 06:38:46 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 06:39:07 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 06:40:15 fileserver dhclient: last message repeated 5 times
Sep 23 06:41:20 fileserver dhclient: last message repeated 5 times
Sep 23 06:42:23 fileserver dhclient: last message repeated 4 times
Sep 23 06:43:31 fileserver dhclient: last message repeated 6 times
Sep 23 06:44:36 fileserver dhclient: last message repeated 5 times
Sep 23 06:45:37 fileserver dhclient: last message repeated 2 times
Sep 23 06:46:37 fileserver dhclient: last message repeated 5 times
Sep 23 06:47:37 fileserver dhclient: last message repeated 6 times
Sep 23 06:48:37 fileserver dhclient: last message repeated 3 times
Sep 23 06:49:37 fileserver dhclient: last message repeated 4 times
Sep 23 06:50:37 fileserver dhclient: last message repeated 5 times
Sep 23 06:51:37 fileserver dhclient: last message repeated 4 times
Sep 23 06:52:37 fileserver dhclient: last message repeated 5 times
Sep 23 06:53:37 fileserver dhclient: last message repeated 5 times
Sep 23 06:54:37 fileserver dhclient: last message repeated 4 times
Sep 23 06:55:37 fileserver dhclient: last message repeated 4 times
Sep 23 06:56:37 fileserver dhclient: last message repeated 5 times
Sep 23 06:57:37 fileserver dhclient: last message repeated 5 times
Sep 23 06:58:37 fileserver dhclient: last message repeated 4 times
Sep 23 06:59:38 fileserver dhclient: last message repeated 5 times
Sep 23 07:00:38 fileserver dhclient: last message repeated 5 times
Sep 23 07:01:38 fileserver dhclient: last message repeated 5 times
Sep 23 07:02:38 fileserver dhclient: last message repeated 5 times
Sep 23 07:03:38 fileserver dhclient: last message repeated 4 times
Sep 23 07:04:38 fileserver dhclient: last message repeated 4 times
Sep 23 07:05:38 fileserver dhclient: last message repeated 4 times
Sep 23 07:06:38 fileserver dhclient: last message repeated 4 times
Sep 23 07:07:38 fileserver dhclient: last message repeated 3 times
Sep 23 07:08:38 fileserver dhclient: last message repeated 5 times
Sep 23 07:08:52 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 07:09:05 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 07:10:08 fileserver dhclient: last message repeated 5 times
Sep 23 07:11:08 fileserver dhclient: last message repeated 3 times
Sep 23 07:12:08 fileserver dhclient: last message repeated 5 times
Sep 23 07:13:08 fileserver dhclient: last message repeated 5 times
Sep 23 07:14:08 fileserver dhclient: last message repeated 5 times
Sep 23 07:15:08 fileserver dhclient: last message repeated 4 times
Sep 23 07:16:08 fileserver dhclient: last message repeated 5 times
Sep 23 07:17:01 fileserver dhclient: last message repeated 3 times
Sep 23 07:17:03 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 07:18:05 fileserver dhclient: last message repeated 4 times
Sep 23 07:19:08 fileserver dhclient: last message repeated 4 times
Sep 23 07:20:09 fileserver dhclient: last message repeated 5 times
Sep 23 07:21:09 fileserver dhclient: last message repeated 5 times
Sep 23 07:22:09 fileserver dhclient: last message repeated 5 times
Sep 23 07:23:09 fileserver dhclient: last message repeated 3 times
Sep 23 07:24:09 fileserver dhclient: last message repeated 4 times
Sep 23 07:25:09 fileserver dhclient: last message repeated 5 times
Sep 23 07:26:09 fileserver dhclient: last message repeated 4 times
Sep 23 07:27:09 fileserver dhclient: last message repeated 4 times
Sep 23 07:28:09 fileserver dhclient: last message repeated 5 times
Sep 23 07:29:09 fileserver dhclient: last message repeated 4 times
Sep 23 07:30:09 fileserver dhclient: last message repeated 5 times
Sep 23 07:31:09 fileserver dhclient: last message repeated 4 times
Sep 23 07:32:09 fileserver dhclient: last message repeated 4 times
Sep 23 07:33:09 fileserver dhclient: last message repeated 5 times
Sep 23 07:34:09 fileserver dhclient: last message repeated 4 times
Sep 23 07:35:09 fileserver dhclient: last message repeated 5 times
Sep 23 07:36:09 fileserver dhclient: last message repeated 5 times
Sep 23 07:37:09 fileserver dhclient: last message repeated 3 times
Sep 23 07:38:09 fileserver dhclient: last message repeated 5 times
Sep 23 07:39:01 fileserver dhclient: last message repeated 3 times
Sep 23 07:39:12 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 07:40:15 fileserver dhclient: last message repeated 6 times
Sep 23 07:41:26 fileserver dhclient: last message repeated 6 times
Sep 23 07:42:37 fileserver dhclient: last message repeated 4 times
Sep 23 07:43:40 fileserver dhclient: last message repeated 4 times
Sep 23 07:44:40 fileserver dhclient: last message repeated 4 times
Sep 23 07:45:40 fileserver dhclient: last message repeated 5 times
Sep 23 07:46:40 fileserver dhclient: last message repeated 4 times
Sep 23 07:47:40 fileserver dhclient: last message repeated 3 times
Sep 23 07:48:40 fileserver dhclient: last message repeated 4 times
Sep 23 07:49:40 fileserver dhclient: last message repeated 4 times
Sep 23 07:50:40 fileserver dhclient: last message repeated 4 times
Sep 23 07:51:40 fileserver dhclient: last message repeated 5 times
Sep 23 07:52:40 fileserver dhclient: last message repeated 4 times
Sep 23 07:53:40 fileserver dhclient: last message repeated 5 times
Sep 23 07:54:40 fileserver dhclient: last message repeated 6 times
Sep 23 07:55:40 fileserver dhclient: last message repeated 4 times
Sep 23 07:56:40 fileserver dhclient: last message repeated 6 times
Sep 23 07:57:40 fileserver dhclient: last message repeated 4 times
Sep 23 07:58:40 fileserver dhclient: last message repeated 5 times
Sep 23 07:59:40 fileserver dhclient: last message repeated 3 times
Sep 23 08:00:41 fileserver dhclient: last message repeated 3 times
Sep 23 08:01:41 fileserver dhclient: last message repeated 5 times
Sep 23 08:02:41 fileserver dhclient: last message repeated 3 times
Sep 23 08:03:41 fileserver dhclient: last message repeated 4 times
Sep 23 08:04:41 fileserver dhclient: last message repeated 4 times
Sep 23 08:05:41 fileserver dhclient: last message repeated 3 times
Sep 23 08:06:41 fileserver dhclient: last message repeated 5 times
Sep 23 08:07:41 fileserver dhclient: last message repeated 4 times
Sep 23 08:08:41 fileserver dhclient: last message repeated 5 times
Sep 23 08:08:59 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 08:09:08 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 08:10:11 fileserver dhclient: last message repeated 3 times
Sep 23 08:11:11 fileserver dhclient: last message repeated 4 times
Sep 23 08:12:11 fileserver dhclient: last message repeated 5 times
Sep 23 08:13:11 fileserver dhclient: last message repeated 5 times
Sep 23 08:14:11 fileserver dhclient: last message repeated 3 times
Sep 23 08:15:11 fileserver dhclient: last message repeated 3 times
Sep 23 08:16:11 fileserver dhclient: last message repeated 4 times
Sep 23 08:17:01 fileserver dhclient: last message repeated 4 times
Sep 23 08:17:12 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 08:18:27 fileserver dhclient: last message repeated 6 times
Sep 23 08:19:30 fileserver dhclient: last message repeated 6 times
Sep 23 08:20:35 fileserver dhclient: last message repeated 5 times
Sep 23 08:21:42 fileserver dhclient: last message repeated 4 times
Sep 23 08:22:42 fileserver dhclient: last message repeated 6 times
Sep 23 08:23:42 fileserver dhclient: last message repeated 3 times
Sep 23 08:24:42 fileserver dhclient: last message repeated 4 times
Sep 23 08:25:42 fileserver dhclient: last message repeated 4 times
Sep 23 08:26:42 fileserver dhclient: last message repeated 4 times
Sep 23 08:27:42 fileserver dhclient: last message repeated 4 times
Sep 23 08:28:42 fileserver dhclient: last message repeated 5 times
Sep 23 08:29:42 fileserver dhclient: last message repeated 6 times
Sep 23 08:30:42 fileserver dhclient: last message repeated 3 times
Sep 23 08:31:42 fileserver dhclient: last message repeated 6 times
Sep 23 08:32:42 fileserver dhclient: last message repeated 5 times
Sep 23 08:33:42 fileserver dhclient: last message repeated 4 times
Sep 23 08:34:42 fileserver dhclient: last message repeated 3 times
Sep 23 08:35:42 fileserver dhclient: last message repeated 5 times
Sep 23 08:36:42 fileserver dhclient: last message repeated 3 times
Sep 23 08:37:42 fileserver dhclient: last message repeated 6 times
Sep 23 08:38:42 fileserver dhclient: last message repeated 4 times
Sep 23 08:38:46 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 08:39:04 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 08:40:08 fileserver dhclient: last message repeated 5 times
Sep 23 08:41:12 fileserver dhclient: last message repeated 4 times
Sep 23 08:42:13 fileserver dhclient: last message repeated 4 times
Sep 23 08:43:13 fileserver dhclient: last message repeated 5 times
Sep 23 08:44:13 fileserver dhclient: last message repeated 4 times
Sep 23 08:45:13 fileserver dhclient: last message repeated 6 times
Sep 23 08:46:13 fileserver dhclient: last message repeated 4 times
Sep 23 08:47:13 fileserver dhclient: last message repeated 4 times
Sep 23 08:48:13 fileserver dhclient: last message repeated 4 times
Sep 23 08:49:13 fileserver dhclient: last message repeated 4 times
Sep 23 08:50:13 fileserver dhclient: last message repeated 4 times
Sep 23 08:51:13 fileserver dhclient: last message repeated 4 times
Sep 23 08:52:13 fileserver dhclient: last message repeated 4 times
Sep 23 08:53:13 fileserver dhclient: last message repeated 6 times
Sep 23 08:54:13 fileserver dhclient: last message repeated 5 times
Sep 23 08:55:13 fileserver dhclient: last message repeated 5 times
Sep 23 08:56:13 fileserver dhclient: last message repeated 4 times
Sep 23 08:57:13 fileserver dhclient: last message repeated 4 times
Sep 23 08:58:13 fileserver dhclient: last message repeated 6 times
Sep 23 08:59:13 fileserver dhclient: last message repeated 5 times
Sep 23 09:00:13 fileserver dhclient: last message repeated 3 times
Sep 23 09:01:13 fileserver dhclient: last message repeated 4 times
Sep 23 09:02:13 fileserver dhclient: last message repeated 4 times
Sep 23 09:03:14 fileserver dhclient: last message repeated 4 times
Sep 23 09:04:14 fileserver dhclient: last message repeated 5 times
Sep 23 09:05:14 fileserver dhclient: last message repeated 5 times
Sep 23 09:06:14 fileserver dhclient: last message repeated 3 times
Sep 23 09:07:14 fileserver dhclient: last message repeated 5 times
Sep 23 09:08:14 fileserver dhclient: last message repeated 5 times
Sep 23 09:09:01 fileserver dhclient: last message repeated 3 times
Sep 23 09:09:09 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 09:10:14 fileserver dhclient: last message repeated 4 times
Sep 23 09:11:14 fileserver dhclient: last message repeated 4 times
Sep 23 09:12:14 fileserver dhclient: last message repeated 3 times
Sep 23 09:13:14 fileserver dhclient: last message repeated 6 times
Sep 23 09:14:14 fileserver dhclient: last message repeated 4 times
Sep 23 09:15:14 fileserver dhclient: last message repeated 5 times
Sep 23 09:16:14 fileserver dhclient: last message repeated 4 times
Sep 23 09:17:01 fileserver dhclient: last message repeated 4 times
Sep 23 09:17:09 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 09:18:10 fileserver dhclient: last message repeated 4 times
Sep 23 09:19:12 fileserver dhclient: last message repeated 5 times
Sep 23 09:20:14 fileserver dhclient: last message repeated 4 times
Sep 23 09:21:14 fileserver dhclient: last message repeated 5 times
Sep 23 09:22:14 fileserver dhclient: last message repeated 5 times
Sep 23 09:23:14 fileserver dhclient: last message repeated 3 times
Sep 23 09:24:15 fileserver dhclient: last message repeated 7 times
Sep 23 09:25:15 fileserver dhclient: last message repeated 3 times
Sep 23 09:26:15 fileserver dhclient: last message repeated 4 times
Sep 23 09:27:15 fileserver dhclient: last message repeated 5 times
Sep 23 09:28:15 fileserver dhclient: last message repeated 5 times
Sep 23 09:29:15 fileserver dhclient: last message repeated 4 times
Sep 23 09:30:15 fileserver dhclient: last message repeated 5 times
Sep 23 09:31:15 fileserver dhclient: last message repeated 4 times
Sep 23 09:32:15 fileserver dhclient: last message repeated 5 times
Sep 23 09:33:15 fileserver dhclient: last message repeated 4 times
Sep 23 09:34:15 fileserver dhclient: last message repeated 5 times
Sep 23 09:35:15 fileserver dhclient: last message repeated 5 times
Sep 23 09:36:15 fileserver dhclient: last message repeated 5 times
Sep 23 09:37:15 fileserver dhclient: last message repeated 4 times
Sep 23 09:38:15 fileserver dhclient: last message repeated 5 times
Sep 23 09:39:01 fileserver dhclient: last message repeated 3 times
Sep 23 09:39:07 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 10.0.1.1 port 67
Sep 23 09:40:15 fileserver dhclient: last message repeated 5 times
Sep 23 09:41:15 fileserver dhclient: last message repeated 5 times
Sep 23 09:42:15 fileserver dhclient: last message repeated 5 times
Sep 23 09:43:15 fileserver dhclient: last message repeated 5 times
Sep 23 09:44:16 fileserver dhclient: last message repeated 3 times
Sep 23 09:45:16 fileserver dhclient: last message repeated 4 times
Sep 23 09:46:16 fileserver dhclient: last message repeated 4 times
Sep 23 09:47:16 fileserver dhclient: last message repeated 6 times
Sep 23 09:48:16 fileserver dhclient: last message repeated 5 times
Sep 23 09:49:16 fileserver dhclient: last message repeated 3 times
Sep 23 09:50:16 fileserver dhclient: last message repeated 5 times
Sep 23 09:51:16 fileserver dhclient: last message repeated 5 times
Sep 23 09:52:16 fileserver dhclient: last message repeated 3 times
Sep 23 09:52:24 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 255.255.255.255 port 67
Sep 23 09:53:30 fileserver dhclient: last message repeated 4 times
Sep 23 09:54:44 fileserver dhclient: last message repeated 5 times
Sep 23 09:55:46 fileserver dhclient: last message repeated 5 times
Sep 23 09:56:46 fileserver dhclient: last message repeated 4 times
Sep 23 09:57:46 fileserver dhclient: last message repeated 5 times
Sep 23 09:58:46 fileserver dhclient: last message repeated 4 times
Sep 23 09:59:46 fileserver dhclient: last message repeated 4 times
Sep 23 10:00:46 fileserver dhclient: last message repeated 5 times
Sep 23 10:01:46 fileserver dhclient: last message repeated 6 times
Sep 23 10:02:46 fileserver dhclient: last message repeated 4 times
Sep 23 10:03:46 fileserver dhclient: last message repeated 5 times
Sep 23 10:04:46 fileserver dhclient: last message repeated 6 times
Sep 23 10:05:47 fileserver dhclient: last message repeated 4 times
Sep 23 10:06:47 fileserver dhclient: last message repeated 5 times
Sep 23 10:07:47 fileserver dhclient: last message repeated 4 times
Sep 23 10:08:47 fileserver dhclient: last message repeated 4 times
Sep 23 10:09:00 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 255.255.255.255 port 67
Sep 23 10:09:15 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 255.255.255.255 port 67
Sep 23 10:10:17 fileserver dhclient: last message repeated 4 times
Sep 23 10:11:17 fileserver dhclient: last message repeated 4 times
Sep 23 10:12:17 fileserver dhclient: last message repeated 3 times
Sep 23 10:13:17 fileserver dhclient: last message repeated 5 times
Sep 23 10:14:17 fileserver dhclient: last message repeated 4 times
Sep 23 10:15:17 fileserver dhclient: last message repeated 4 times
Sep 23 10:16:17 fileserver dhclient: last message repeated 6 times
Sep 23 10:17:01 fileserver dhclient: last message repeated 3 times
Sep 23 10:17:16 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 255.255.255.255 port 67
Sep 23 10:18:17 fileserver dhclient: last message repeated 3 times
Sep 23 10:19:17 fileserver dhclient: last message repeated 4 times
Sep 23 10:20:17 fileserver dhclient: last message repeated 5 times
Sep 23 10:21:17 fileserver dhclient: last message repeated 4 times
Sep 23 10:22:17 fileserver dhclient: last message repeated 6 times
Sep 23 10:23:17 fileserver dhclient: last message repeated 4 times
Sep 23 10:24:17 fileserver dhclient: last message repeated 4 times
Sep 23 10:25:18 fileserver dhclient: last message repeated 5 times
Sep 23 10:26:18 fileserver dhclient: last message repeated 6 times
Sep 23 10:27:18 fileserver dhclient: last message repeated 5 times
Sep 23 10:28:18 fileserver dhclient: last message repeated 3 times
Sep 23 10:29:18 fileserver dhclient: last message repeated 5 times
Sep 23 10:30:18 fileserver dhclient: last message repeated 4 times
Sep 23 10:31:18 fileserver dhclient: last message repeated 4 times
Sep 23 10:32:18 fileserver dhclient: last message repeated 3 times
Sep 23 10:33:18 fileserver dhclient: last message repeated 6 times
Sep 23 10:34:18 fileserver dhclient: last message repeated 6 times
Sep 23 10:35:18 fileserver dhclient: last message repeated 4 times
Sep 23 10:36:18 fileserver dhclient: last message repeated 4 times
Sep 23 10:37:18 fileserver dhclient: last message repeated 4 times
Sep 23 10:38:18 fileserver dhclient: last message repeated 5 times
Sep 23 10:39:01 fileserver dhclient: last message repeated 4 times
Sep 23 10:39:12 fileserver dhclient: DHCPREQUEST of 10.0.1.24 on eth0 to 255.255.255.255 port 67
Sep 23 10:40:18 fileserver dhclient: last message repeated 5 times
Sep 23 10:41:18 fileserver dhclient: last message repeated 5 times
Sep 23 10:42:18 fileserver dhclient: last message repeated 6 times
Sep 23 10:43:18 fileserver dhclient: last message repeated 4 times
Sep 23 10:44:18 fileserver dhclient: last message repeated 4 times
Sep 23 10:45:18 fileserver dhclient: last message repeated 4 times
Sep 23 10:46:18 fileserver dhclient: last message repeated 5 times
Sep 23 10:47:19 fileserver dhclient: last message repeated 5 times
Sep 23 10:48:19 fileserver dhclient: last message repeated 4 times
Sep 23 10:49:19 fileserver dhclient: last message repeated 4 times
Sep 23 10:50:19 fileserver dhclient: last message repeated 6 times
Sep 23 10:51:19 fileserver dhclient: last message repeated 4 times
Sep 23 10:52:19 fileserver dhclient: last message repeated 4 times
Sep 23 10:53:19 fileserver dhclient: last message repeated 5 times
Sep 23 10:54:19 fileserver dhclient: last message repeated 5 times
Sep 23 10:55:19 fileserver dhclient: last message repeated 3 times
Sep 23 10:56:19 fileserver dhclient: last message repeated 4 times
Sep 23 10:57:19 fileserver dhclient: last message repeated 3 times
Sep 23 10:58:19 fileserver dhclient: last message repeated 5 times
Sep 23 10:59:19 fileserver dhclient: last message repeated 5 times
Sep 23 11:00:19 fileserver dhclient: last message repeated 5 times
```

ps aux | grep dhc:

```
root       613  0.0  0.2   2548   644 ?        Ss   Sep18   0:04 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
dave      8277  0.0  0.3   4156   856 pts/0    S+   11:01   0:00 grep --color=auto dhc
```

---

### Post by CharlesA on 2011-09-23
Have you rebooted since changing the ip to static?

Seems that dhclient is still running and grabbing an ip from dhcp when the lease expires.

---

### Post by arbulus on 2011-09-23
> **CharlesA said:**
> Have you rebooted since changing the ip to static?

Seems that dhclient is still running and grabbing an ip from dhcp when the lease expires.

I hadn't rebooted. I didn't even think of that until papibe asked. I have rebooted now, so I'll see if that makes a difference.

Thanks everyone for your help!

---

