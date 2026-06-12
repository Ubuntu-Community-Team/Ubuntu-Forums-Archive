---
title: "Limit bandwidth option doesn't work"
date: 2010-02-09
forum: Ubuntu One (CLOSED)
---

### Post by jondecker76 on 2010-02-09
The limit bandwidth options in U1 don't work for me. I will check the checkboxes and change the values. When I come back later, they are back to being unchecked, with the default values filled back in.

Is this a known issue?

---

### Post by duanedesign on 2010-02-11
jondecker76,
Yes this is a known issue. I can point you towards the bug report where you can monitor the progress of this  bug as well as find any workarounds.
[bug 509740]("https://bugs.edge.launchpad.net/ubuntuone-client/+bug/509740")

Here is the workaround from the Bug report.
WORK AROUND

1. Quit the Ubuntu One client
2. Delete the file: ~/.config/ubuntuone/syncdaemon.conf
    (If using Nautilus, make sure you do a Ctrl-H to view hidden files when in your home directory)
3. Start the Ubuntu One client

You can try resetting the bandwidth usage preferences but if you continue to run into problems, follow the steps above and don't turn the limit bandwidth usage on for the time being.

---

### Post by srf21c on 2011-11-02
The Ubuntu one client on may 11.10 system will retain the set bandwidth limit values. The bandwidth usage however is not being limited and it's choking my upstream traffic.

---

### Post by mbewley on 2011-11-13
I also have this problem - the ubuntu one client does remember bandwidth settings, but checking via the system monitor, it doesn't respect the limits I set. Being on asynchronous ADSL, the effect is that when U1 is uploading, I effectively can't use the internet, as the upstream traffic chokes anything going downstream. So, I have this annoying state where I need to manually disable U1 whenever I want to use the internet, unless it's perfectly in sync.
1) Is there a workaround to this?
2) Is there a fix planned for the client?

---

### Post by Rincewind on 2011-11-14
A workaround I use successfully is to install wondershaper from the repositories, the syntax is then:

```
sudo wondershaper eth0 downspeed upspeed
```

- replace eth0 with your network interface in use and downspeed and upspeed are in bits, so my ADSL is 512kbit up and I don't typically want to limit downspeed, so I use an arbitrarily large number for that option as follows:

```
sudo wondershaper eth0 10000000 512
```

Hope that helps in the meantime while the bug gets fixed...

---

