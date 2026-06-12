---
title: "how to &quot;restart&quot; the bridge"
date: 2016-03-08
forum: Virtualisation
---

### Post by Romu on 2016-03-08
Hi,
I run a VMs server which is powered by Ubuntu 15.10. This server has 2 ethernet adapter. And both adapters are connected to separate networks.

The first adapter has been setup with its own bridge when the server was first installed.

Now, I'm trying to setup the second adapter, also with its own bridge. This second bridge is setup in the same way as the first, only the network settings are different. My problem is I made a mistake in the bridge IP address. I've corrected the error, but I can't restart the bridge. If I do:

```
sudo ifdown br1
```

I get: ```
interface br1 not configured
```

I can down & up the physical link (eno2 in this case), but that doesn't change anything. Is there any solution to take my configuration into account without restarting the server?

Thanks.

---

### Post by MAFoElffen on 2016-03-08
br1 is not the physical device... try to reset the physical device name and the new bridge settings for that device should get picked up for it:
```

sudo ifdown eth1 && sudo ifup eth1

```

---

### Post by Romu on 2016-03-08
Thanks for the help, but as I wrote:

> **Romu said:**
> I can down & up the physical link (eno2 in this case), but that doesn't change anything.

---

### Post by houstonbofh on 2016-03-08
You can restart networking itself, and it is much faster then rebooting.

sudo service networking restart

---

### Post by Romu on 2016-03-11
Thanks. Indeed, it doesn't work. I suspect a bug in 15.10, because the /etc/network/interfaces file is only taken into account at reboot. Strange.

---

### Post by MAFoElffen on 2016-03-12
You just mentioned that your were running 15.10, so... I think it also takes into account whether you have the bridge setup as net.cfg or net-ctl. The where and hopw your bridge is setup. (for instance openvswitch)

15.10 used more pieces of systemd. Where things where starting to be setup differently under the hood. what if you query your bridges using brctl?
```

sudo brctl show

```
Which, buried in it's docs, says if there are problems with a bridge in brctl, then try these 2 commands
```

sudo ifconfig ethn 0 0.0.0.0
sudo ifconfig ethn promisc up

```
...substituting 'ethn' for the port name.

---

