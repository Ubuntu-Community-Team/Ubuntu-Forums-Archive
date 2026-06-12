---
title: "VirtualBox, Ubuntu as guest and multicast problem"
date: 2017-11-18
forum: Virtualisation
---

### Post by marcecastro on 2017-11-18
Hi there!

My setup:


[LIST]
[*]Host: Win7, running VirtualBox 5.1.30
[*]Guest: Ubuntu Server 16.04, bridged adapter
[*]Software: running Home Assistant on Ubuntu
[/LIST]

Home Assistant is not working properly because multicast packages are not being received. I have tested Home Assistant on another machine (out of VirtualBox) and it does work well (multicast works).

So I'm guessing my static IP setup could be the culprit:
/etc/network/interfaces:

```

auto enp0s3
iface enp0s3 inet static
address 192.168.1.158
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.4.4 8.8.8.8
```

Any ideas? Thanks!

---

### Post by SeijiSensei on 2017-11-19
There are a lot of pages about VirtualBox and multicast:  [https://www.google.com/search?q=multicast+virtualbox](https://www.google.com/search?q=multicast+virtualbox)

---

### Post by marcecastro on 2017-11-19
> **SeijiSensei said:**
> There are a lot of pages about VirtualBox and multicast:  [https://www.google.com/search?q=multicast+virtualbox](https://www.google.com/search?q=multicast+virtualbox)

Thanks for taking the time to reply. But seriously? You're just LMGTFYing me? I'm asking here because I've already googled it and read tons of threads about VirtualBox/Multicast. The thing is I couldn't find any error on my VB setup, so I'm just guessing my interfaces configuration on Ubuntu may be the reason.

---

### Post by SeijiSensei on 2017-11-20
Sorry.  From long experience, the number of people who post here without searching for more relevant help elsewhere is pretty high.

Is the Windows machine running a firewall?  Maybe that is filtering out the multicast traffic.  I know the VM is directly on the network via the bridged adapter, but maybe Windows gets in the way?  

The Linux VM isn't running a firewall, right?

---

### Post by marcecastro on 2017-11-20
> **SeijiSensei said:**
> Sorry.  From long experience, the number of people who post here without searching for more relevant help elsewhere is pretty high.

Is the Windows machine running a firewall?  Maybe that is filtering out the multicast traffic.  I know the VM is directly on the network via the bridged adapter, but maybe Windows gets in the way?  

The Linux VM isn't running a firewall, right?

No worries :-) The Windows machine is not running the firewall. I tested removing the static IP on the Ubuntu virtual machine, but it didn't work either. I've been further testing and it looks like the Windows machine may also rejecting the multicast packets. I don't know for sure yet. But I think it's not because of my Ubuntu machine. 

Thanks for the taking the time to respond!

---

