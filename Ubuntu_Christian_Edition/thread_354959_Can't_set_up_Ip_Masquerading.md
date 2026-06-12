---
title: "Can't set up Ip Masquerading"
date: 2007-02-06
forum: Ubuntu Christian Edition
---

### Post by andytof47 on 2007-02-06
Hey first of all,

Love your work especially the DansGuardian gui, smoooooooooth and sweeeeeeeeeeet

Next love Ubuntu CE

Trying to use it on my desktop system as a server because it has a few things I like already buiolt into it

only I have run into a couple of probs

1st) 

/proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied

so i tried, but it still hasn't worked

sudo sysctl -w net.ipv4.ip_forward=1


any help

My system is using an atheros wlan card in Master mode with 2 other NICs rt8139's

2nd) basic firewall script returns this error

./00firewal.sh: 1: !/bin/sh: not found

again any way of helping this brother out?

I would prefer to use this version as my server / gateway because it seems to be locked down a little tighter in regards to Porn than what i can currently set up my self, this is good becuase then I won't be able to get around it (I have struggled with this issue ) I used ipcops as my gateway for ages and it's worked perfectly, but it is somewhat limited in what you can get in terms of addons etc...So i would very much like to see if this can be resolved


Love your work):P

---

### Post by p!=f on 2007-02-06
> **andytof47 said:**
> 
1st) 

/proc/sys/net/ipv4/ip_forward
bash: /proc/sys/net/ipv4/ip_forward: Permission denied

```

sudo -i
echo "1" > /proc/sys/net/ipv4/ip_forward

```

> **andytof47 said:**
> 
so i tried, but it still hasn't worked

sudo sysctl -w net.ipv4.ip_forward=1

It enables ip forwarding, not masquerading (NAT).
You will need something like this in your firewall script
```

/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```
where eth0 is your internet interface or you may 
```

apt-cache show shorewall guarddog guidedog firestarter

```
I recommend shorewall. It doesn't come with a GUI but configuration files are well commented, you may also use predefined examples for 1, 2 and 3 interface setups. Firestarter is for GNOME and guarddog and guidedog for KDE.

> **andytof47 said:**
> 
My system is using an atheros wlan card in Master mode with 2 other NICs rt8139's

2nd) basic firewall script returns this error

./00firewal.sh: 1: !/bin/sh: not found

again any way of helping this brother out?

Should be
```

#!/bin/sh

```
:)

Hope it helps.

---

### Post by andytof47 on 2007-02-06
[SIZE="6"]Cheers:)  Will give it a go soon[/SIZE]

---

