---
title: "Have to manually start init.d/networking ?"
date: 2012-01-24
forum: Server Platforms
---

### Post by Revo- on 2012-01-24
As per the below screenshot, networking does not automatically start on this one server (a VM).

I have to run /etc/init.d/networking restart    to get the interfaces to come up.

[IMG]http://i.imgur.com/IVDhc.png[/IMG]


The interface config looks like this:

```
The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 172.xx.xx.xx
        netmask 255.255.248.0
        network 172.xx.xx.xx
        broadcast 172.xx.xx.xx
        gateway 172.xx.xx.xx
```
Does anyone know what I should do to get networking to start up on boot?


Many thakns

---

### Post by rubylaser on 2012-01-24
This [thread]("http://ubuntuforums.org/showthread.php?t=1859643") covers your problem and has a solution in [post 6]("http://ubuntuforums.org/showpost.php?p=11344530&postcount=6").

---

### Post by rubylaser on 2012-01-24
It would make sense to mark this Thread as Solved since you responded to the thread that I linked to instead of this one :)

---

