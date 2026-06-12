---
title: "[SOLVED] VBox Bridge group breaks NFS server?"
date: 2008-06-07
forum: Server Platforms
---

### Post by scottburton11 on 2008-06-07
I have a box running Hardy 8.04 with two NICs - eth0 connected to an internal network, serving NFS, and eth1 with a public IP as a webserver.

I created a bridge group, gave eth1 0.0.0.0, gave br0 my public IP, added eth1 to the bridge group, and added a virtual port vbox0 as per the various VirtualBox documentation. 

When I restart networking, it restarts nfs-kernel-server too, and now clients on the local net can't bind to the NFS server, RPC craps out: 

```
Cannot MNT RPC: RPC: Program not registered
```

 I'm not trying to serve NFS to br0 or eth1... Is there something incompatible about bridging and NFS?

---

### Post by scottburton11 on 2008-06-09
Just following up.

I don't know what broke nfs-kernel-server on this machine, but it was more or less unresponsive suddenly. I retraced my steps to before the problem started, and it didn't shed much light. It is working now, though. 

Here's what happened:

1. I uninstalled [strikethrough]Network Mangler[/strikethrough] Network Manager, since it was conflicting with the ifconfig and iproute2 tools. Added 'killall network-manager' etc. to rc.local

2. I removed eth1's configuration, brought it down, and brought it back up with address 0.0.0.0

3. I used brctl to create a new bridge br0, and add eth1 to it.

4. I gave br0 a public IP, used VBoxAddIF to add a virtual interface to br0, and brought it up. Verified that br0 is functional.


This is where the trouble started. NFS daemons died, and I started getting rpc bind errors - first something to the effect of "Cannot determine hostname <myhost>", and then the dreaded "RPC Error: Program not registered". Restarting nfs-kernel-server did nothing, and restarting networking complained about RPC as well. 

I reversed the above steps to see where I went wrong, and nothing fixed it. Finally I re-installed portmap, nfs-kernel-server and nfs-common, and it's back up again.


Any ideas what could have caused all of this? Is it still OK to remove Network Mangler? I'm only exporting nfs to networks on eth0 - do creating bridge groups with other interfaces affect nfs at all? Still pretty stumped.

---

### Post by starfry on 2008-09-22
Hi, did you get anywhere with this?

I just tried setting up Vbox on my laptop using my trusty configuration that's been working on my desktop for ages. 

I have the nfs issue you mention and I believe it has something to do with Network Manager (which I don't use on my desktop).

Any pointers would be appreciated...

---

