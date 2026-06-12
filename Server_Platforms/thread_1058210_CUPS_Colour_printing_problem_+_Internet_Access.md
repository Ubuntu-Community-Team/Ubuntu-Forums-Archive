---
title: "CUPS Colour printing problem + Internet Access"
date: 2009-02-02
forum: Server Platforms
---

### Post by CyberAxe on 2009-02-02
I'm running Ubuntu Server 8.10, I'm having some trouble with the internet all computers connected to the server can connect to the internet fine but the server itself doesn&#8217;t (which is very annoying as i have ddclient running on it to update the OpenDNS server IP), I can get it working by changing the name servers and then restarting the server (perhaps its just the reboot that fixes it) but after a week or so it stops working again, does anyone know how to fix this?

I also have 2 printers setup with cups and shared through samba all the computers connected to the printers that are shared are using the latest cups drivers form the website (these are all windows machines) but only print black and white both are Kyocera mita I believe but I don&#8217;t have the exact model numbers on me at the moment one is black and white and the other is colour but they all print in greyscale on the colour and there is no colour options in the print settings on the windows options

---

### Post by CyberAxe on 2009-02-08
anyone?

---

### Post by cariboo on 2009-02-08
I'm not sure what you problem is with your network connection dropping, but you don't have to reboot the computer every time the connection drops, at the prompt type:

```
sudo /etc/init.d/networking restart
```

Have you checked any of the logs for indications of what is happening. A simple check of:

```
dmesg | tail -n10
```

might show up something about your network connection.

Jim

---

### Post by CyberAxe on 2009-02-10
> **cariboo907 said:**
> I'm not sure what you problem is with your network connection dropping, but you don't have to reboot the computer every time the connection drops, at the prompt type:

```
sudo /etc/init.d/networking restart
```

Have you checked any of the logs for indications of what is happening. A simple check of:

```
dmesg | tail -n10
```

might show up something about your network connection.

Jim

Thanks for the reply, i forgot to test that today so will ahve to wait till next monday, though it seems to be working since i rebooted it last tuesday

The Main problem now is the Colour printing

---

### Post by CyberAxe on 2009-02-18
It's doing still doing it. the output from that command is thus

```

[   24.418342] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   25.255488] NET: Registered protocol family 10
[   25.256933] lo: Disabled Privacy Extensions
[   28.739431] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   29.179016] ppdev: user-space parallel port driver
[   33.566962] NET: Registered protocol family 17
[   36.150155] eth0: no IPv6 routers present
[1285427.675022] ecryptfs_parse_options: eCryptfs: unrecognized option 'rw'
[1285427.675054] ecryptfs_parse_options: eCryptfs: unrecognized option 'user=administrator'
[1285428.176636] padlock: VIA PadLock not detected.

```

Though it may now have been lack of refresh info in the conf file, just updated that and will have to wait to see if it had worked.

I think the problems with the printers may be that guest users dont have the persmissions to do stuff as i noticed samba pemissions in the log file was bringing up an error for nobody users when trying to delete printer queues

Thanks

---

