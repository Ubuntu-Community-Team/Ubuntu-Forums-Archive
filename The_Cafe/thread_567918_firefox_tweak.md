---
title: "firefox tweak?"
date: 2007-10-05
forum: The Cafe
---

### Post by kerry_s on 2007-10-05
i think i found a little tweak. my firefox no longer uses 100% on startup and seems to start faster for the first startup.

can some one else try?

sudo your-editor /etc/sysctrl.conf
uncomment
```
net/ipv4/icmp_echo_ignore_broadcasts=1
kernel.printk = 4 4 1 7
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1
net.ipv4.tcp_syncookies=1
net.ipv4.conf.default.forwarding=1
```
reboot

start firefox
notice a difference?

---

### Post by Lord Illidan on 2007-10-05
What do those lines do?

---

### Post by kerry_s on 2007-10-05
i'm just going to copy and paste the relevant section, instead of linking all over.

```

3.4.2. icmp_echo_ignore_broadcasts

This variable works precisely the same as icmp_echo_ignore_all except that it will only ignore those ICMP messages sent to broadcast or multicast addresses. It should be quite obvious why this is good, it would among other things stop this specific host from being part of smurf attacks and likely problems. Broadcast pings are generally bad unless you are using this to find out how many hosts on your network(s) are up or not.

The icmp_echo_ignore_broadcasts variable takes a boolean value and is per default turned off. If you want to turn this value on, you should do so since there is relatively few bad sides to not replying to broadcast pings. 

```

```
kernel.printk-> stop low-level messages on console
```

```

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

```

```

# Uncomment the next line to enable TCP/IP SYN cookies
net.ipv4.tcp_syncookies=1

```

```

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.conf.default.forwarding=1

```

---

