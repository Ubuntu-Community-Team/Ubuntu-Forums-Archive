---
title: "Cannot set network interfaces"
date: 2011-09-23
forum: Server Platforms
---

### Post by ph3ar on 2011-09-23
Hello,

I have configured a list of eth aliases with static ips to /etc/network/interfaces like:
```
auto eth0
iface eth0 inet static
	address XXX.XXX.XXX.XXX
	netmask XXX.XXX.XXX.XXX
	gateway XXX.XXX.XXX.XXX

auto eth0:2
iface eth0:2 inet static
	address XXX.XXX.XXX.XXX
	netmask XXX.XXX.XXX.XXX

auto eth0:4
iface eth0:4 inet static
	address XXX.XXX.XXX.XXX
	netmask XXX.XXX.XXX.XXX

```
Normally one edits the file and removes the interface from the config file (/etc/network/interfaces) restarting the network service with:
```
/etc/init.d/networking restart
```
or
```
service networking restart
```

... and it should work but unexpectedly the removed interface (eth0:2) comes back after a while although it's not included in the config file /etc/network/interfaces .

I also used the sync command to flush the file system buffers (I don't know if it's relevant).

Note that it worked when I made a reboot or with this cmd:
```
id addr flush
```

Normally this shouldn't happen.

Any ideas? of why this is happening and a possible resolution except reboot or flush?

System: Ubuntu 10.04.3 LTS

Thanks

---

### Post by volkswagner on 2011-09-23
Just a shot it the dark here...

Do you have a trail in /etc/udev/rules.d/70-persistent-net.rules.  If you do you may want to comment out or delete the entry and restart.

```
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by ph3ar on 2011-09-26
Thanks for your reply volkswagner.

There is nothing relevant in /etc/udev/rules.d/70-persistent-net.rules file.

Any more ideas?

---

### Post by Azdour on 2011-09-26
Hi,

More shots in the dark :)

Could it be the network-manager (if its installed), may be its remembering eth0:2 and doing something to bring it back?

Does this still occur after a reboot?

Is there anything in the logs regarding eth0:2?

---

### Post by ph3ar on 2011-09-27
> **Azdour said:**
> 
Could it be the network-manager (if its installed), may be its remembering eth0:2 and doing something to bring it back?

Does this still occur after a reboot?

Is there anything in the logs regarding eth0:2?

Thanks for your reply Azdour,

Network manager is not installed.
I haven't see anything regarding this interface at the logs.

After a reboot the interfaces keep up with the the config file /etc/network/interfaces

---

### Post by Azdour on 2011-09-27
Hi,

I've run out of ideas. I was going to suggest avahi incase it is publishing the network eth0:2 and it comes back because avahi does something. But I'm not sure how it works or even if it can bring back network interfaces. If you able to reproduce the issue of eth0:2 reappearing does eth0:2 appear when you type:

```
avahi-browse -a
```

---

### Post by ph3ar on 2011-09-27
Unfortunately I cannot reproduce the problem.
I was just wondering why this is happening.

I will stick to this when I'm updating the /etc/network/interfaces configuration:
```
ip addr flush eth0 ; /etc/init.d/networking restart
```

---

