---
title: "troubleshoot network hangs 10.04 running in VirtualBox"
date: 2012-03-12
forum: Virtualisation
---

### Post by bfromcolo on 2012-03-12
I am running Ubuntu 10.04 64 bit in a VirtualBox (v4.1.8 ), host OS is Win 7 64-bit.  Everything was fine for a month, but for the past week or so I am experiencing intermittent network hangs in Firefox and Chrome when browsing.  These will last from 30 seconds to a few minutes, and usually the request will complete normally, all will be fine after the hang.  These hangs do not affect the host system and this is not occurring with a copy of Win 8 that I also run in VirtualBox.  I don't know how to trouble shoot whats happening, any help would be appreciated.  I guess I could just reinstall, but it would be nice to understand whats happening.

Thanks

---

### Post by jayshomebrew on 2012-03-13
Is your virtualbox set up as a bridged network, or NAT?

Like all network issues, you need to find where it is disconnecting, ie, is it a DNS issue, a hardware cable disconnect, wireless connection, firewall issue, IP conflict.

I suggest changing your guest system to be a bridged network, then you can ping your system directly from your host. Next time it disconnects, try and ping both directions, ie ping ubuntu.ip from W7 and ping host.ip

[IMG]http://opensourceexperiments.files.wordpress.com/2008/04/ping-vm1-and-vm2-from-a-vm.jpg[/IMG]

If your pinging works, then maybe its DNS. Try wget from within ubuntu:
```
wget www.ubuntu.com
--2012-03-12 21:00:51--  http://www.ubuntu.com/
Resolving www.ubuntu.com... 91.189.90.41
Connecting to www.ubuntu.com|91.189.90.41|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 37233 (36K) [text/html]
Saving to: `index.html'

100%[======================================>] 37,233      77.7K/s   in 0.5s    

2012-03-12 21:00:57 (77.7 KB/s) - `index.html' saved [37233/37233]

```

---

