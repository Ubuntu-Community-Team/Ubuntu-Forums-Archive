---
title: "wicd on Focal Fossa"
date: 2024-11-14
forum: Ubuntu/Debian BASED
---

### Post by marktrent2 on 2024-11-14
I have a bit of a special situation on my hands. I have FossaDog, a Puppy Linux version of Focal Fossa. It's basically Fossa with some additional applications that make our lives easier in a "frugal" installation. I particularly like the "frugal" approach.

Among their many customizations, they included a network manager called Frisbee. I don't like it. I like wicd-gtk. I really like wicd-gtk. I used wicd-gtk a lot on Debian back in the day and it always worked flawlessly. So I cheated and brought wicd-gtk from the Bionic repository. It installed, no conflicts, and it runs. Yay! And it can see my ethernet connection and my wifi card and access points nearby, and it seems to connect. It absolutely looks and behaves like it connects. It even says "connected" in the status bar for a split  second. But then it says "Not connected."

Firsbee is a script. I inspected it and couldn't figure out what special magic it does. Trying to fix the problem, I tried "ifup eth0" but the output says eth0 doesn't exist. But it does. Then I edited /etc/network/interfaces:

```

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address         192.168.1.101
    netmask         255.255.255.0
    network         192.168.1.0
    broadcast       192.168.1.255
    gateway         192.168.1.1
    dns-nameservers 192.168.1.1 8.8.8.8
    dns-domain example.com
    dns-search example.com

```

It still doesn't work.

Is there something I can do to sort this out?

---

### Post by howefield on 2024-11-14
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by marktrent2 on 2024-11-15
I've discovered that the internet is working after the system is rebooted. Then wicd-gtk can disconnect, but cannot connect again. One thing that works for reconnecting is 'service dhcpcd restart'. But that is bad. I want to use wicd-gtk to connnect and disconnect at leisure.

---

