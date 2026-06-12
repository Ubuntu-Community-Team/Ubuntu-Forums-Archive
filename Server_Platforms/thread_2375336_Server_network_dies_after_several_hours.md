---
title: "Server network dies after several hours"
date: 2017-10-23
forum: Server Platforms
---

### Post by timonoj on 2017-10-23
Hi guys!

I have an ubuntu headless server that has been working very reliably for a couple of years. However recently (last ten days?) it started dying on me very frequently, every day or two tops. Sometimes after just passing the night, the server is dead. If I access via local console (it's a VM) I can still reach it, but it will still crash trying to reboot, it dies when trying to unmount the NFS shares, which I guess it can't reach anymore due to the network dying. If I try to restart the network it also crashes. What can I do to avoid this? How can I troubleshoot this to actually know what's going on?
Server uses:
Seafile, dynamic DNS, crashplan backup (this crap eats RAM for breakfast), transmission and that's about it.

Thanks a lot!

---

### Post by Ciberjohn on 2017-10-24
Hi.
What does your kernel.log file says ?

---

### Post by timonoj on 2017-10-24
Hi, thanks for the reply!
> 
Oct 23 19:23:16 SeafileServer kernel: [14434.377003] IPv4: martian source 192.168.0.5 from 192.168.0.5, on dev ens18
Oct 23 19:23:16 SeafileServer kernel: [14434.377006] ll header: 00000000: [server's MAC ADDRESS]        ......,MT.%...
Oct 23 19:23:18 SeafileServer kernel: [14436.785447] IPv4: martian source 192.168.0.5 from 192.168.0.5, on dev ens18
Oct 23 19:23:18 SeafileServer kernel: [14436.785450] ll header: 00000000: [server's MAC ADDRESS]        ......,MT.%...
Oct 23 19:23:18 SeafileServer kernel: [14436.786107] IPv4: martian source 192.168.0.5 from 192.168.0.5, on dev ens18
Oct 23 19:23:18 SeafileServer kernel: [14436.786108] ll header: 00000000: [server's MAC ADDRESS]        ......,MT.%...
Oct 23 19:23:19 SeafileServer kernel: [14438.294442] IPv4: martian source 192.168.0.5 from 192.168.0.5, on dev ens18
Oct 23 19:23:19 SeafileServer kernel: [14438.294455] ll header: 00000000: [server's MAC ADDRESS]        ......,MT.%...
Oct 23 19:23:21 SeafileServer kernel: [14439.820295] IPv4: martian source 192.168.0.5 from 192.168.0.5, on dev ens18
Oct 23 19:23:21 SeafileServer kernel: [14439.820312] ll header: 00000000: [server's MAC ADDRESS]        ......,MT.%...
Oct 23 19:23:21 SeafileServer kernel: [14439.820340] IPv4: martian source 192.168.0.5 from 192.168.0.5, on dev ens18
Oct 23 19:23:21 SeafileServer kernel: [14439.820344] ll header: 00000000: [server's MAC ADDRESS]        ......,MT.%...
Oct 24 04:36:13 SeafileServer kernel: [47612.651078] TCP: ens18: Driver has suspect GRO implementation, TCP performance may be compromised.
Oct 24 05:24:53 SeafileServer kernel: [50532.208817] lockd: server 192.168.0.10 not responding, still trying
Oct 24 05:26:47 SeafileServer kernel: [50646.897391] nfs: server 192.168.0.10 not responding, still trying
Oct 24 05:26:47 SeafileServer kernel: [50646.897405] nfs: server 192.168.0.10 not responding, still trying
Oct 24 05:26:47 SeafileServer kernel: [50646.897407] nfs: server 192.168.0.10 not responding, still trying
Oct 24 05:26:47 SeafileServer kernel: [50646.897410] nfs: server 192.168.0.10 not responding, still trying
Oct 24 05:26:47 SeafileServer kernel: [50646.897412] nfs: server 192.168.0.10 not responding, still trying
Oct 24 05:26:47 SeafileServer kernel: [50646.897414] nfs: server 192.168.0.10 not responding, still trying

What's with the Martian address? 192.168.0.5 is the server address, and 192.168.0.10 is the NFS storage. The server is set so nginx faces the internet with a dynamic DNS domain. So far it never gave me trouble in years.

To be more detailed, I think it doesn't pinpoint the moment the network crashes. I mean, by then I believe I noticed the network was down, and from the console I tried a manual ifupdown, but got hanged halfway. I think I tried a reboot, and then hanged on the NFS shutdown. The log goes on, and shows other cases where after a bunch of those martian source messages the next thing you see is the server startup logs, so, it means it went with a hard reset after being unresponsive.

---

### Post by timonoj on 2017-10-30
Another error I'm getting in console is the following:
> 
/etc/host.conf: line 4: bad command 'nospoof on'


My host.conf is the default one I believe:
> 
order hosts,bind
multi on
nospoof on


What is going on? I recently upgraded from 17.04 to 17.10, but I'm not sure it mentioned any changes to the host.conf file.

---

