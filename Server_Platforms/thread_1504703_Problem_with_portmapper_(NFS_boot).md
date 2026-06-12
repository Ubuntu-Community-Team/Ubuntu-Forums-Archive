---
title: "Problem with portmapper (NFS boot)"
date: 2010-06-08
forum: Server Platforms
---

### Post by tom_tlr on 2010-06-08
Hi,

I try to make a small AVR-Board boot a Linux from my Lenovo laptop, which is configured as NFS server (running nfs-kernel-server). Everything is configured correctly and it should work, but it doesn't.
I just installed another laptop (from ASUS) with the same configuration (OS, tools, settings...) and there it works immediately.

So I wondered, what's going on on eth0 ?
I checked with Wireshark and here are the things I found out.
On both laptops, the following paket arrives:
```
Protocol   |  Info
------------------------------------------------------------
Portmap    |  V2 GETPORT Call MOUNT(100005) V:1 UDP
```

2 seconds later, the Lenovo receives this paket again and after that nothing else happens.
The ASUS laptop on the other hand returns the following thing right after the first "GETPORT Call" paket.

```
Portmap    |  V2 GETPORT Reply (Call In 3) Port:44781
```

It seams, something's interfering with the portmapper on the Lenovo laptop. Both files hosts.deny and hosts.allow are empty and modifying the hosts.allow didn't help.

Any ideas what it could be?

Best regards,
Andreas

---

### Post by suseendran.rengabashyam on 2010-06-09
Hi,

You can take a look at this thread

[http://ubuntuforums.org/showthread.php?t=1407246](http://ubuntuforums.org/showthread.php?t=1407246)

it might give you some idea in configuring the NFS Server.

Hope this helps.

---

