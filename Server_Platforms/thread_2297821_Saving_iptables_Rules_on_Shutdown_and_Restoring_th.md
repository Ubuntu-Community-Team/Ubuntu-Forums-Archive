---
title: "Saving iptables Rules on Shutdown and Restoring them on Boot Automatically"
date: 2015-10-06
forum: Server Platforms
---

### Post by own3mall on 2015-10-06
I noticed that when a server restarts, the iptables rules are reset and flushed back to their original state.  I was looking for a way to permanently preserve my current iptables rules automatically without me doing any work.  

I found a package called iptables-persistent, but in my opinion, it is not truly "persistent" out of the box.   iptables-persistent does NOT automatically save the system's current iptables rules on shutdown or reboot.  It only saves when you tell it to save.

Therefore, I modified the source for iptables-persistent to make it automatically save the current iptables rules when the server shutsdown (halts), reboots, or enters runlevel 1.  It restores the rules in runlevels 2-5.  Essentially, this modified version of iptables-persistent saves the rules on shutdown automatically and restores them on boot.  

If you want to use this modified version, here's how you can get it.

```
sudo apt-get remove iptables-persistent
sudo dpkg -r iptables-persistent
wget http://dinofly.com/files/linux/iptables-persistent_0.5.8_all.deb
sudo dpkg --install iptables-persistent_0.5.8_all.deb

```

Please use the above at your own risk because it is not official by any means.  I've tested my updated deb package in Ubuntu 12.04, 14.04, and 15.04.  It worked in all of them.  I hope this will help someone looking to keep their rules truly persistent even when the system is shutdown or rebooted.  It also appears to work in conjunction with fail2ban.  If anyone can think of why this is a bad idea, please let me know.

---

### Post by Habitual on 2015-10-07
I use fail2ban also and this is what have in my notes.
in /etc/network/interfaces
 ```
pre-up iptables-restore < /etc/iptables/rules.v4
post-down iptables-save > /etc/iptables/rules.v4
```

Did you do this also?
I don't believe merely installing that package is enough.

unless "your deb" ???? takes care of that...?

---

### Post by own3mall on 2015-10-07
> **Habitual said:**
> I use fail2ban also and this is what have in my notes.
in /etc/network/interfaces
 ```
pre-up iptables-restore < /etc/iptables/rules.v4
post-down iptables-save > /etc/iptables/rules.v4
```

Did you do this also?
I don't believe merely installing that package is enough.

unless "your deb" ???? takes care of that...?

The deb does the same thing, except that it saves the rules on shutdown or reboot (using iptables-save) and restores the rules on boot (using iptables-restore).

It's independent of the network interfaces configuration.  Your setup essentially does the same thing though.  iptables-persistent saves ipv6 rules if there are any, and so does my deb.

Hadn't thought about doing it your way... thanks!  Either way should work.

---

### Post by Habitual on 2015-10-07
Glad I could 'help'. :)

---

