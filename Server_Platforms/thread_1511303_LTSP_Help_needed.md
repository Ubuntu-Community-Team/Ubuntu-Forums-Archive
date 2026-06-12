---
title: "LTSP Help needed"
date: 2010-06-16
forum: Server Platforms
---

### Post by v4169sgr on 2010-06-16
Dear All,

I've previously posted about problems with 10.04, LTSP and Optiplex GX110 clients - see [http://ubuntuforums.org/showthread.php?t=1501761]("http://http://ubuntuforums.org/showthread.php?t=1501761").

I now have a second-hand HP T5525 thin client, in good working order.

A plus is that when PXE booting I can now see the screen. The big minus is that I cannot get past the splash screen. No login, no nothing. :confused:

This has shown:

a. The problem exists independently of the type of client;
b. [From previous experience] We know that 8.04 clients boot from 8.04 servers;
c. Other people have reported HP T5525s work fine for them [possible login / compiz issues, but nothing like this];

I've probably stuffed up somewhere, but am not sure where. I've set all back to defaults: /var/lib/tftboot/ltsp/i386/pxeconfig.cfg/default is as per the default, and there is no lts.conf in the path.

/var/log/syslog shows

```
Jun 16 21:21:15 aammscott dhcpd: DHCPDISCOVER from 00:16:35:7e:44:43 via eth0
Jun 16 21:21:16 aammscott dhcpd: DHCPOFFER on 10.0.0.23 to 00:16:35:7e:44:43 via eth0
Jun 16 21:21:17 aammscott dhcpd: DHCPREQUEST for 10.0.0.23 (10.0.0.1) from 00:16:35:7e:44:43 via eth0
Jun 16 21:21:17 aammscott dhcpd: DHCPACK on 10.0.0.23 to 00:16:35:7e:44:43 via eth0
Jun 16 21:21:17 aammscott in.tftpd[2482]: tftp: client does not accept options
Jun 16 21:21:27 aammscott dhcpd: DHCPDISCOVER from 00:16:35:7e:44:43 via eth0
Jun 16 21:21:27 aammscott dhcpd: DHCPOFFER on 10.0.0.23 to 00:16:35:7e:44:43 via eth0
Jun 16 21:21:27 aammscott dhcpd: DHCPREQUEST for 10.0.0.23 (10.0.0.1) from 00:16:35:7e:44:43 via eth0
Jun 16 21:21:27 aammscott dhcpd: DHCPACK on 10.0.0.23 to 00:16:35:7e:44:43 via eth0
Jun 16 21:21:27 aammscott nbd_server[1416]: connect from 10.0.0.23, assigned file is /opt/ltsp/i386
Jun 16 21:21:27 aammscott nbd_server[1416]: Can't open authorization file (null) (Bad address).
Jun 16 21:21:27 aammscott nbd_server[1416]: Authorized client
Jun 16 21:21:27 aammscott nbd_server[2497]: Starting to serve
Jun 16 21:21:27 aammscott nbd_server[2497]: Size of exported file/device is 4096

```

How can I find out what is going wrong and why?

Thanks!

---

### Post by v4169sgr on 2010-06-16
Should have added that the client is pingable from the server when the splash screen is showing i.e. we have networking, and that key combinations on the client do NOT result in a login prompt.

---

### Post by v4169sgr on 2010-06-16
XDMCP works on the T5525 client, following [http://http://ubuntuforums.org/showthread.php?t=1471703&highlight=XDMCP]("http://http://ubuntuforums.org/showthread.php?t=1471703&highlight=XDMCP"), but I'd much prefer to get PXE boot working if at all possible, as XDMCP has serious disadvantages [naff screen resolution, no sound, poor performance ...].

---

