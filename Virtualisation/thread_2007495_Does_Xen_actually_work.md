---
title: "Does Xen actually work ?"
date: 2012-06-20
forum: Virtualisation
---

### Post by WitchCraft on 2012-06-20
Can anybody answer my two questions here:

[http://askubuntu.com/questions/153869/whats-fould-with-my-xen-config](http://askubuntu.com/questions/153869/whats-fould-with-my-xen-config)

and

[http://askubuntu.com/questions/153868/help-with-xen-bridging-trouble](http://askubuntu.com/questions/153868/help-with-xen-bridging-trouble)

---

### Post by CharlesA on 2012-06-20
Both are dead links.

Take a look here:
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

---

### Post by WitchCraft on 2012-06-20
Right, I just managed to solve these, after hours of trying.
So I deleted them.


The only remaining problem is that it doesn't work with a WIFI interface.

I have exactly the same configuration on my server and my laptop.
On the server, I add this to /etc/network/interfaces
```

auto xenbr0
iface xenbr0 inet dhcp
        bridge_ports eth0

```


On my laptop, I need to take wlan0 instead of eth0:
```

auto xenbr0
iface xenbr0 inet dhcp
        bridge_ports wlan0

```

On the server it works, on the laptop I get:
operation not supported.

Apparently because the wifi-card cannot be set into master mode.
However, I really doubt that, as iw lists AP (access point) as a supported mode. This is probably some bogus bug with the new MAC80211 driver.

Right now I'm exprimenting with hostapd, as this tool must set the network card into master mode
```

hostapd -d -B /etc/hostapd/hostapd.conf

```

However, something is very wrong...

---

### Post by CharlesA on 2012-06-20
I've not tried to bridge wireless before.

Did you see this?
[http://virt.kernelnewbies.org/XenWifiNetwork](http://virt.kernelnewbies.org/XenWifiNetwork)

---

### Post by WitchCraft on 2012-06-21
> **CharlesA said:**
> I've not tried to bridge wireless before.

Did you see this?
[http://virt.kernelnewbies.org/XenWifiNetwork](http://virt.kernelnewbies.org/XenWifiNetwork)

Is this supposed to be a joke ?
It's untested and looking at it, I have
a) seen that the author was unable to install xen
b) seen that he's using NAT instead of bridging (which already works without this)
c) seen that he's working with eth0 and eth1 and not wlan0
d) no idea what the idea behind this is
e) no clue as to why this should work

---

### Post by CharlesA on 2012-06-21
> **WitchCraft said:**
> Is this supposed to be a joke ?

Apparently. It was the second hit on Google. ;)

First hit is here:
[http://wiki.xen.org/wiki/Main_Page](http://wiki.xen.org/wiki/Main_Page)

As for master mode, read here:
[https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)

---

### Post by WitchCraft on 2012-06-23
> **CharlesA said:**
> Apparently. It was the second hit on Google. ;)

First hit is here:
[http://wiki.xen.org/wiki/Main_Page](http://wiki.xen.org/wiki/Main_Page)

As for master mode, read here:
[https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)

Apparently, you seem to be under the impression that I didn't Google my problem before I posted here.

I assure you this is not the case.
I already read those unfortunately rather useless pages a while ago (well I admit, not everything of course, as I don't have a few decades to spare).

Unfortunately, the problem is a bit long to describe.
I posted an entire Xen howto in the tutorials section, but it will take a little time until it is approved.

Bottom line is:
The real problem is, that apparently Linux-Kernel >= 2.6.33 won't let you bridge a wireless interface in managed mode at all unless you enable 4addr.

But the version of iw in the Ubuntu 11.10 repositories (0.9x) is so outdated (4 years old), that it doesn't even recognize the command
```

iw dev wlan0 set 4addr on

```

One first needs to download version 3.4 from
```

http://linuxwireless.org/download/iw/

```
then compile and install it until one can do that.

Afterwards, the entire network breaks down (bug in network-manager or in the Linux kernel?)

I haven't been able to get this working, although 
```

brctl addif br0 wlan0

```
now works with 4addr on

and 
```

brctl show 

```
now shows xenbr0 as bridged to wlan0.

Just that now there is no internet connection on wlan0.
(ip address shows fine).


BTW, as completely unrelated rant, with the new xen-kernel, my laptop now crashes every time when it should come-back from stand-by. With the normal kernel, this worked fine.

---

### Post by WitchCraft on 2012-06-24
OK, the tutorial has been OK'ed, so you find the rest of the info here:
 
[http://ubuntuforums.org/showthread.php?t=2008795](http://ubuntuforums.org/showthread.php?t=2008795)

---

