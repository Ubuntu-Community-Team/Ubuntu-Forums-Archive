---
title: "Server drops static IP and interface comes back up as DHCP"
date: 2008-05-02
forum: Server Platforms
---

### Post by Maxtorm on 2008-05-02
This was happening to me under 7.10 and I thought the issue would be fixed under 8.04. No such luck. My interfaces file looks like this:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 207.81.162.204
        netmask 255.255.255.0
        gateway 207.81.162.1
```
Pretty normal, right? When I went to access the server today at .204, it didn't respond. I went to the server physically and logged on and lo and behold, the server had switched to DHCP. However, the interfaces file hadn't changed. Indeed, doing an ifdown eth0 and ifup eth0 brought the server back up at the static address. For the time being, I setup a cron job to do an ifdown/ifup at midnight every night, but that isn't a good long-term solution. Anyone have any ideas?

---

### Post by Deathrend on 2008-05-02
See if this helps

[http://ubuntuforums.org/showthread.php?t=337693](http://ubuntuforums.org/showthread.php?t=337693)

---

### Post by Maxtorm on 2008-05-02
I'm having one of those days. Just posted my reply to the other thread by accident. Thanks Deathrend.

---

