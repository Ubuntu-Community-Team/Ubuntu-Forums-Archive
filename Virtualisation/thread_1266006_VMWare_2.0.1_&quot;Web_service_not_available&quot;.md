---
title: "VMWare 2.0.1 &quot;Web service not available&quot;"
date: 2009-09-14
forum: Virtualisation
---

### Post by CurlyChris on 2009-09-14
Hi

I've also been fighting with VMWare 2.0.1 for quite a while and searching all over for a possible solution.  I've installed it in Jaunty with patch for vmware-config.pl applied and installation and configuration go through with no errors.  I've also disabled ipv6 as described in various threads in this forum.

When I log in ([http://localhost:8222/ui/#](http://localhost:8222/ui/#)) it spends up to about 50 seconds displaying the main screen, with "loading" in the bottom pane, then the page appears to fully load for a split-second, after which the screen clears and an error box is displayed with the detail:
> ServiceNotAvailableException: Web service not available.

tail /var/log/syslog contains:
```
Sep 14 09:46:20 chris-laptop /usr/lib/vmware/bin/vmware-hostd[3782]: Accepted password for user chris from 127.0.0.1
Sep 14 09:47:28 chris-laptop vmnetBridge: RTM_NEWLINK: name:eth1 index:3 flags:0x00011043 
Sep 14 09:47:28 chris-laptop vmnetBridge: Can't add interface eth1 3 (does exist). 

```

(eth1 is the wireless card on the laptop.)

If anyone can offer any insight into what I need to do next to try to get this to work, I'd be very grateful.

And yes, I know that VMWare server 2.* is generally loathed but I haven't yet found where I can download v. 1.0.? to install instead if there isn't another solution to this.

And, for some unknown reason, I can't get the Windows-only software I use for work installed onto XP in VirtualBox, otherwise I wouldn't be messing around with this!

Thanks in advance! :)

Chris

---

