---
title: "[SOLVED] Samba share on an USB NTFS disk"
date: 2008-10-07
forum: Server Platforms
---

### Post by gjosef on 2008-10-07
Hi, I am using Ubuntu Desktop 8.04 and trying to share files on an external USB hard drive through Samba. Have installed GSAMBAD, and set up my shares so they all work. However, the shares do become available automatically when the computer boots, only after I have logged in, activated the external hard drive and restarted SAMBA (using the buttons "activate" and "deactivate" in GSAMBAD 0.1.9).

So I am looking for some advice on how to fix this.

I understand I must put my USB drive in the /etc/fstab file to make it automount. Have done this and the hard drive is now available when I login to the system. (although I'm not sure if I got the flags right):
[INDENT]LABEL=LaCie  /media/LaCie  ntfs  users,auto,exec  0  0[/INDENT]

Still, the Samba shares are not available on the LAN. When I start GSAMBAD, it says "Status: Activated, inactive servers: nmbd". If I deactivate and reactivate the service, the complaint about nmbd disappears and the shares work as expected.

Anyone who could give me some good advice?
My suspicion is that the samba service starts before that the USB hard drive has been mounted, but I'm not that experienced with Linux, so I can't say for sure.

Thanks in Advance

---

### Post by lykwydchykyn on 2008-10-07
from /var/log/samba, can you post log.smbd and log.nmbd?  Also, maybe have a look at /var/log/syslog for potential samba errors.

---

### Post by gjosef on 2008-10-07
Here is log.smbd:

```
[2008/10/06 17:14:30, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/06 17:14:31, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/06 17:14:31, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 07:34:13, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 07:34:13, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 07:34:13, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 07:36:29, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 07:36:29, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 07:36:29, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 09:17:42, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 09:17:43, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 09:17:43, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 09:20:32, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 09:20:32, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 09:20:32, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 11:13:44, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 11:13:44, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 11:13:44, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 11:30:36, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 11:30:36, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 11:30:36, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 11:41:15, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 11:41:15, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 11:41:15, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 15:32:57, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 15:32:57, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 15:32:57, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 16:05:25, 0] smbd/server.c:main(944)
  smbd version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 16:05:25, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
[2008/10/07 16:05:25, 0] printing/pcap.c:pcap_cache_reload(159)
  Unable to open printcap file /etc/printcap for read!
```

and here comes log.nmbd:

```
[2008/10/06 17:14:31, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 00:14:58, 0] nmbd/nmbd.c:terminate(58)
  Got SIGTERM: going down...
[2008/10/07 07:34:13, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 07:34:13, 0] nmbd/nmbd_subnetdb.c:create_subnets(245)
  create_subnets: unable to create any subnet from given interfaces. nmbd is terminating
[2008/10/07 07:34:13, 0] nmbd/nmbd.c:main(795)
  ERROR: Failed when creating subnet lists. Exiting.
[2008/10/07 07:36:29, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 09:16:38, 0] nmbd/nmbd.c:terminate(58)
  Got SIGTERM: going down...
[2008/10/07 09:17:42, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 09:17:42, 0] nmbd/nmbd_subnetdb.c:create_subnets(245)
  create_subnets: unable to create any subnet from given interfaces. nmbd is terminating
[2008/10/07 09:17:42, 0] nmbd/nmbd.c:main(795)
  ERROR: Failed when creating subnet lists. Exiting.
[2008/10/07 09:20:32, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 11:12:39, 0] nmbd/nmbd.c:terminate(58)
  Got SIGTERM: going down...
[2008/10/07 11:13:43, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 11:13:43, 0] nmbd/nmbd_subnetdb.c:create_subnets(245)
  create_subnets: unable to create any subnet from given interfaces. nmbd is terminating
[2008/10/07 11:13:43, 0] nmbd/nmbd.c:main(795)
  ERROR: Failed when creating subnet lists. Exiting.
[2008/10/07 11:30:36, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 11:41:15, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 15:32:57, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008
[2008/10/07 15:32:57, 0] nmbd/nmbd_subnetdb.c:create_subnets(245)
  create_subnets: unable to create any subnet from given interfaces. nmbd is terminating
[2008/10/07 15:32:57, 0] nmbd/nmbd.c:main(795)
  ERROR: Failed when creating subnet lists. Exiting.
[2008/10/07 16:05:25, 0] nmbd/nmbd.c:main(721)
  Netbios nameserver version 3.0.28a started.
  Copyright Andrew Tridgell and the Samba Team 1992-2008

```

I see there is a message about subnets in the log.nmbd. Might this be a clue?

---

### Post by lykwydchykyn on 2008-10-07
When you say the shares aren't available on the LAN, do you mean that you just can't browse to them?  Can you connect to it directly from a shortcut or mapped drive?

nmbd is just a daemon that takes care of netbios name resolution; it doesn't actually have anything to do with publishing the shared folders (that's smbd's job).  But if something were screwy with nmbd, you'd have trouble browsing to the folders, but you could still connect directly I would think.

---

### Post by gjosef on 2008-10-08
> **lykwydchykyn said:**
> When you say the shares aren't available on the LAN, do you mean that you just can't browse to them?  Can you connect to it directly from a shortcut or mapped drive?

No, the entire samba service is unavailable. Using the direct address (\\server\share) does not work.

> **lykwydchykyn said:**
> nmbd is just a daemon that takes care of netbios name resolution; it doesn't actually have anything to do with publishing the shared folders (that's smbd's job).  But if something were screwy with nmbd, you'd have trouble browsing to the folders, but you could still connect directly I would think.

Another thing I came to think about is that I have two network cards in the computer. One built-in 100 mbit/s card, and one pcmcia-based 1gbit/s card. I use the latter as main network interface. Could the problem be that the latter gets activated after the samba service has been started or something like that?

---

### Post by gjosef on 2008-10-08
I think I solved the problem.

I went into the Network Settings dialog box and saw that my two network interfaces (both the 100mbps and the 1gbps) were set for "Roaming mode enabled". I disabled this and put the 1gbps card to Automatic Configuration by DHCP, and voilà, it worked on boot.

Thanks lykwydchykyn for your time and advice.

---

