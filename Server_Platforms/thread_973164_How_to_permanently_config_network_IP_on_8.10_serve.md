---
title: "How to permanently config network IP on 8.10 server edition?"
date: 2008-11-06
forum: Server Platforms
---

### Post by bobmct on 2008-11-06
I've performed a fresh install of this edition but for what ever reason I cannot keep my static IP set.  If I use ifconfig it starts to work but reverts back to dhcp and I loose my connection.

Can someone please advise what tool(s) to use to accomplish this as well as perhaps other system settings?

TIA:confused:

---

### Post by bagpussnz on 2008-11-06
Hi,
we've seen that too on our ubuntu servers. 

Look for a process called dhclient and kill it. Even though you have set a static ip, dhclient seems to change it to dhcp when it thinks the lease runs out.

Either that or do a reboot (in which case dhclient won't be restarted).

Cheers,
Ian.

---

### Post by lykwydchykyn on 2008-11-06
edit the file /etc/network/interfaces

you probably have a line like this:
```

iface eth0 inet dhcp

```
Change it to something like this:
```

iface eth0 inet static
  address 192.168.1.42
  netmask 255.255.255.0
  gateway 192.168.1.1

```
then do:
```

/etc/init.d/networking restart

```

Obviously, fill in the correct ip/netmask/gateway for your network.

---

### Post by y@w on 2008-11-06
Actually, if you're just using ifconfig to change the IP, you'll need to follow the steps in both of these posts..

You'll have to configure /etc/network/interfaces with the static IP information so it stays with the machine after a networking or machine restart. Plus, the first time that you change it to a static IP, the dhcp client will remain running. It will change the IP whenever it checks in regardless of what's in the interfaces config file. A simple 'ps aux | grep dhcp' will find the dhcp client PID. Then you can use kill to stop it.

---

### Post by cariboo on 2008-11-06
If you are using Gnome Desktop and Network Manager, you will have to uninstall Network Manager and set your static ip address in /etc/network/interfaces, as there is a bug in network manager that doesn't allow you to save settings that you set manually.

Jim

---

### Post by adamcrosby on 2008-11-24
The Network Manager thing is a pain in the neck on the desktop edition too.
Is this scheduled to be fixed any time soon?

---

### Post by CrucifiedEgo on 2008-11-24
Well, uh, we would fix it, but, you see...

...have a seat right over there.

(supposedly, this is fixed: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/256054](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/256054))

---

### Post by cariboo on 2008-11-24
I updated my sever to Interid about a week and a half ago and to get a static ip address I just uninstalled dhcp3-client and have had no problems since.

Jim

---

