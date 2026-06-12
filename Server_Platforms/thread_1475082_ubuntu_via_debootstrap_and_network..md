---
title: "ubuntu via debootstrap and network."
date: 2010-05-06
forum: Server Platforms
---

### Post by gooood on 2010-05-06
Ok, here is the situation:
I am trying to install ubuntu 10.04 via debootstrap remotely on my server.
I have a netboot mode with access to my disks, and apparently I have installed everything successfully. I also have a "vKVM", wich basically runs the server on emulation so oyu can see what's going on without network on the server.
The problem is that when I reboot the network doesn't start. I started a discussion on the provider forum, but I couldn't solve the problem: [http://forum.ovh.co.uk/showthread.php?p=30484](http://forum.ovh.co.uk/showthread.php?p=30484)

The problem seems to be that eth0 gets renamed in eth1 in the boot sequence. The other problem is that it doesn't work even if I put eth1 instead of eth0 in network/interfaces.

I am really frustrated at this point, does someone have a clue of what's going on?

Thanks in advance.

---

