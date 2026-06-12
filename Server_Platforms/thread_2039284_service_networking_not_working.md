---
title: "service networking not working"
date: 2012-08-08
forum: Server Platforms
---

### Post by cyanne on 2012-08-08
I was trying to make some adjustments to my /etc/networking/interfaces file so I could use IPv6. My ISP gave me an IPv6 block so that's not an issue. It will start up just fine but if I try to make adjustments to the interface file and then use "service networking restart" I get the error message "networking stop/waiting"

I also tired ifup eth0 and got "Failed to bring up eth0." ifdown eth0 nets me "ifdown: interface eth0 not configured"

So my only recourse is to reboot my server entirely every time I want to implement a change and see if it worked. Is this a bug or am I doing something wrong?

---

### Post by rukiaEnix on 2012-08-08
Please post  your interfaces file.

---

### Post by cyanne on 2012-08-08
The IPv6 stuff was added as instructed by my VPS provider. This interface file does work, as long as I don't try to use 'service networking restart' or '/etc/init.d/networking restart'. On a fresh reboot, I can easily ping address 2605:4500:2:23b5::1.

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 204.62.15.38
        gateway 204.62.15.1
        netmask 255.255.255.0

auto eth1
iface eth1 inet static
        address 10.9.1.162
        netmask 255.255.0.0
iface eth0 inet6 static
        address 2605:4500:2:23b5::1
        netmask 64
        up ip -6 route add 2605:4500:2::2 dev eth0
        down ip -6 route del 2605:4500:2::2 dev eth0

```

---

### Post by rukiaEnix on 2012-08-08
Let's try messing around with the file :)

The last two lines is for adding the gateway? If it is for that replace them with:

```

gateway6 *address*

```

And now restart. 

Sometimes I think trial and error is the best.

Or you could try this post I made for the configuration ([http://rukiaenix.blogspot.mx/2012/07/configuracion-basica-de-red-ipv6-en.html](http://rukiaenix.blogspot.mx/2012/07/configuracion-basica-de-red-ipv6-en.html)). It is in Spanish but just look at the interfaces configuration.

Your configuration seems good but we might be skipping something and when you have something wrong in the interfaces file the network service acts weird.

---

### Post by cyanne on 2012-08-08
Changed my interfaces file to read

```

iface eth0 inet6 static
        pre-up modprobe ipv6
        address 2605:4500:2:23b5::1
        netmask 64
        gateway 2605:4500:2::2

```

Instead of 
```

iface eth0 inet6 static
        address 2605:4500:2:23b5::1
        netmask 64
        up ip -6 route add 2605:4500:2::2 dev eth0
        down ip -6 route del 2605:4500:2::2 dev eth0

```

Still no go. I read somewhere that service networking might have a bug in it..?

---

### Post by rukiaEnix on 2012-08-08
Let's make this last try before checking the logs for something:

Remove this:

```

pre-up modprobe ipv6

```

And change this:

```

gateway 2605:4500:2::2

```

To this:

```

gateway6 2605:4500:2::2

```

---

### Post by cyanne on 2012-08-08
Still the same error messages.

---

### Post by rukiaEnix on 2012-08-08
OK.

Check in **/var/log** for the file **messages** or **syslog** and check them to find if they have some info about the networking service.

---

### Post by cyanne on 2012-08-08
I see some messages about withdrawing address records...

---

### Post by rukiaEnix on 2012-08-08
Please post what you found at the log.

---

### Post by cyanne on 2012-08-09
I see something similar to below repeatedly. 
```
Aug  8 11:31:36 brigid avahi-daemon[730]: Withdrawing address record for 10.9.1.162 on eth1.
Aug  8 11:31:36 brigid avahi-daemon[730]: Leaving mDNS multicast group on interface eth1.IPv4 with address 10.9.1.162.
Aug  8 11:31:36 brigid avahi-daemon[730]: Interface eth1.IPv4 no longer relevant for mDNS.
Aug  8 11:31:36 brigid avahi-daemon[730]: Interface eth1.IPv6 no longer relevant for mDNS.
Aug  8 11:31:36 brigid avahi-daemon[730]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::5054:ff:fe2a:1058.
Aug  8 11:31:36 brigid avahi-daemon[730]: Withdrawing address record for fe80::5054:ff:fe2a:1058 on eth1.
Aug  8 11:31:36 brigid avahi-daemon[730]: Joining mDNS multicast group on interface eth1.IPv4 with address 10.9.1.162.
Aug  8 11:31:36 brigid avahi-daemon[730]: New relevant interface eth1.IPv4 for mDNS.
Aug  8 11:31:36 brigid avahi-daemon[730]: Registering new address record for 10.9.1.162 on eth1.IPv4.
Aug  8 11:31:38 brigid avahi-daemon[730]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::5054:ff:fe2a:1058.
Aug  8 11:31:38 brigid avahi-daemon[730]: New relevant interface eth1.IPv6 for mDNS.
Aug  8 11:31:38 brigid avahi-daemon[730]: Registering new address record for fe80::5054:ff:fe2a:1058 on eth1.*.
```

But only ever see it with interface eth0 when I do a full reboot.

---

