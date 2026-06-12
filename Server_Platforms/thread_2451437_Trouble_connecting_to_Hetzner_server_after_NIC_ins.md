---
title: "Trouble connecting to Hetzner server after NIC installation"
date: 2020-10-04
forum: Server Platforms
---

### Post by ShotTard on 2020-10-04
Hi,






I was having some network stability issues on my new Hetzner dedicated server, so I decided to order a 1Gbit Intel NIC, as all my previous Hetzner servers had one.


The Server is running Ubuntu Server 20.04.






After the NIC was installed, I could no longer connect to the server. I remembered reading a post somewhere saying that you'd need to change some system configurations after getting a new NIC.


I've activated the Debian rescue system which Hetzner provides and have chrooted into Ubuntu. It's been a few years since I've been in a similar situation, so I'm a little lost.


I tried to change the interface name in the "netplan" conf file, I'm not sure if that's the right move, and I'm also not sure of the naming scheme.


Stock netplan conf: [https://pastebin.com/KeDe9M0R](https://pastebin.com/KeDe9M0R)


I tried changing "enp3s0" to "enp3s1", "enp4s0" and "ens4" (the last one was the interface name in the virtual kvm.


I couldn't find any info about the new NIC in the Journalctl bootlog: [https://pastebin.com/9WgvS3Gj](https://pastebin.com/9WgvS3Gj)


Lspci from the rescue system (had some trouble setting up networking in the chroot, in order to properly install lspci): [https://pastebin.com/TP4Aww0Z](https://pastebin.com/TP4Aww0Z)






Any assistance would be much appreciated.


Thanks

---

### Post by TheFu on 2020-10-04
Run
```
lshw -c network
```
to get a list of network device names and the drivers.  Appears you have 2 NICs installed.
[LIST=1]
[*]great Intel PRO/1000
[*]Not so great Realtek 8111h
[/LIST]

I didn't see that lspci shows the device name.  That's the first step. 
If hetzner has special needs, I know nothing about that. I only know standard ubuntu.

Best to post text in these forums. Just wrap it with **code-tags** to keep the original formatting. That is in the advanced editor, if you need buttons.

---

### Post by ShotTard on 2020-10-05
> **TheFu said:**
> 

Best to post text in these forums. Just wrap it with **code-tags** to keep the original formatting. That is in the advanced editor, if you need buttons.

Thanks, I'll keep that in mind next time.

Hetzner didn't have any available KVMs (to get the correct interface name), so they fixed it for me.

---

