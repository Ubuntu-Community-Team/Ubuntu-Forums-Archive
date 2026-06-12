---
title: "static IP won't stay put"
date: 2008-01-07
forum: Server Platforms
---

### Post by Pitt Stains on 2008-01-07
Hello,

I have one server that refuses to hold onto its assigned IP address.  I'm not sure what I'm doing wrong here.  Here is the /etc/network/interfaces for that machine:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.10.10.60
netmask 255.255.255.0
network 10.10.10.0
broadcast 10.10.10.255
gateway 10.10.10.1

```

Sometimes I come in after a weekend and discover that the server has acquired a DHCP address (e.g., 10.10.10.106).  It's a pretty new install (less than a month old) and there aren't any cron jobs.  I'm also the only person with access to the machine.

It's easy to fix (sudo ifdown eth0, then sudo ifup eth0), but I shouldn't have to do this.

Any ideas what is going on?  Thanks!

---

### Post by digitalbenji on 2008-01-07
are you running X windows with a network manager?  The graphical network manager applications don't read from /etc/network (though they aught to).  If you are running one, use its GUI to configure the static IP as well, and I expect that would resolve the problem.

Let us know if it works, thanks,

---

### Post by Pitt Stains on 2008-01-07
> **digitalbenji said:**
> are you running X windows with a network manager?  The graphical network manager applications don't read from /etc/network (though they aught to).  If you are running one, use its GUI to configure the static IP as well, and I expect that would resolve the problem.

Let us know if it works, thanks,

I guess I should have specified that I'm running Ubuntu 7.10 Server.  There's no GUI.  Thanks.

[EDIT] I should also add that the intended configuration (the static address) does take, and it sticks for a few days, but it seems to revert to DHCP once or twice a week.

[EDIT #2] **_Update_: I just checked the other systems on the network, and it seems they've all had their IP addresses changed.**  Most of the machines on the network are non-technical users who are allowed to connect via DHCP; I don't care what IP address they are assigned.  For this reason, the router is set up to assign addresses dynamically.  However, I have systems running services that need to have static addresses, so for these I've edited the /etc/network/interfaces files to assign the addresses.  This has worked for me in other environments, but here it seems that the router eventually assigns new addresses to my machines every few days.  Does anyone know why this is or how to work around it?

---

### Post by p_quarles on 2008-01-07
Is it possible that a DHCP server on the network is trying to occasionally reassign an address to this machine? 

Anyway, I've found that with some routers, it's necessary to "reserve" a network address for the machine that needs it before you can get a reliable static address.

---

### Post by Pitt Stains on 2008-01-07
> **p_quarles said:**
> Is it possible that a DHCP server on the network is trying to occasionally reassign an address to this machine? 

Anyway, I've found that with some routers, it's necessary to "reserve" a network address for the machine that needs it before you can get a reliable static address.

Hmmm, well, the DHCP range is 10.10.10.100 to 10.10.10.149, and I am assigning the static addresses in the range 10.10.10.55 to 10.10.10.65, so there shouldn't be any conflict.  I'm looking at the router now to see if there's a way to "reserve" IP addresses.

---

### Post by cdenley on 2008-01-07
Have you rebooted the servers since configuring them to have a static ip? You shouldn't have to do this, but maybe the dhcp client is running when it shouldn't. You can try this command, I think it will kill any instances of the dhcp client.
```

sudo killall dhclient

```

You have restarted networking, right?
```

sudo /etc/init.d/networking restart

```

---

### Post by Pitt Stains on 2008-01-07
> **cdenley said:**
> Have you rebooted the servers since configuring them to have a static ip? You shouldn't have to do this, but maybe the dhcp client is running when it shouldn't. You can try this command, I think it will kill any instances of the dhcp client.
```

sudo killall dhclient

```

You have restarted networking, right?
```

sudo /etc/init.d/networking restart

```

The output for
```

sudo killall dhclient

```
was:
```

dhclient: no process killed

```

I don't believe I've restarted networking.  That's probably a good idea, and I guess it makes sense that the machines would still look for addresses from the DHCP server until networking is restarted (all I did is ifdown and ifup after configuring).  Since configuring the static IP, I don't think I've rebooted the machines either.  I guess I'll do this instead of restarting networking, as these are new servers and there is nothing mission-critical going on with them.

I'll post again if the addresses start changing on their own.  If you don't hear from me within a week or so, I guess everything is going well.

Thanks for the support!

---

### Post by ryanradford on 2008-04-21
Couple of thoughts, I am having the same problem.

On my system, I did a 'ps auxw | grep dhclient' and found the following line:
dhcp 3657 0.0 0.0 2416 872 ? S<s Apr15 0:00 dhclient3 ie IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

This is after I tried the killall of dhclient and it told me there was no process. Then I tried killall of dhcp, still no process. So I killed the pid of 3657 and the process is dead now.

didnot@myserver:/var/log$ sudo kill 3657
(replace numbers with your PID number).
I am assuming that when I changed to static and never rebooted, the process was still running for dhcp, and it for whatever reason overwrote the static IP address.

---

### Post by nkassi on 2008-04-21
The process won't die with killall dhclient. Use ps aux | grep "dhclient" and it will list the process. Then use kill with the process id.

---

