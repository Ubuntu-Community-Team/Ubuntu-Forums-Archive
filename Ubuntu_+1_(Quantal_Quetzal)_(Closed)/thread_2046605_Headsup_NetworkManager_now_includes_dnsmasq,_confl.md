---
title: "Headsup: NetworkManager now includes dnsmasq, conflicts with manually installed versi"
date: 2012-08-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jfernyhough on 2012-08-23
I've had dnsmasq installed for years to cache DNS requests. It's always worked well and there was a bug/wishlist item submitted for NetworkManager to do caching.

Looks like it's happened.

I updated to find a complete lack of DNS resolving unless I stopped dnsmasq ($ sudo service dnsmasq stop), and found another process running bound to 127.0.1.1:

$ ps aux | grep dns
nobody    2022  0.0  0.0  28876  1532 ?        S    12:47   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/nm-dns-dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d

So, yeah. If you have problems with DNS not resolving try stopping dnsmasq. :D

I've now apt-get remove'd the manual install of dnsmasq from my quantal machines and the caching is still happening, so I'm happy I guess?

---

### Post by jfernyhough on 2012-08-23
This may also have screwed up DNS in NAT-connected VirtualBox machines... grr...

--edit
Oh, no, just needed to remove the prepend 127.0.0.1 from /etc/dhcp/dhclient.conf and reconnect the LAN connection (all on the host).

--edit 2
Or not. Gah.

---

### Post by jfernyhough on 2012-08-23
Turns out this has been in the wings for while: [http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

Not sure why only now it's biting me in the behind.

---

### Post by dino99 on 2012-08-23
At first glance this has followed that upgrade:

network-manager (0.9.6.0-0ubuntu4) quantal; urgency=low

  * debian/patches/dns-dnsmasq-interface-and-dbus-path.patch: set the address
    dnsmasq (and bind) plugins should listen on for DNS resolution to 127.0.1.1,
    as opposed to 127.0.0.1 to avoid conflicts with other instances that might
    need to run on the system with that address.
    Also set the dnsmasq DBus service name to our own custom name:
    org.freedesktop.NetworkManager.dnsmasq, which will also avoid conflicting
    with other dnsmasq instances which might have --enable-dbus enabled.
    (LP: #1034946)

 -- Mathieu Trudel-Lapierre <mathieu-tl@ubuntu.com>  Tue, 21 Aug 2012 11:45:46 -0400

---

### Post by jfernyhough on 2012-08-23
Yup, just found this in the changelog:

dnsmasq (2.63-1ubuntu1) quantal; urgency=low
    * Merge with Debian unstable; remaining changes: 
    - debian/control: dnsmasq-base Breaks/Replaces dnsmasq (<< 2.62-3ubuntu1) 
      due to the dbus config file move. 

So it's borkwn. Nice to know. :D

---

### Post by jfernyhough on 2012-08-23
OK, so after doing some digging it looks like dnsmasq will not run and listen on 127.0.0.1:53 as it used to. Instead it runs on (e.g.) 192.168.0.1:53. Trying to force the interface to 127.0.0.1 makes no difference and dnsmasq fails to run correctly (service start says OK but it doesn't listen on port 53 ($ sudo netstat -nl46p | grep :53 ).

Without changing the interface in dnsmasq.conf, on starting it sets /etc/resolv.conf to 127.0.0.1, where nothing is listening, also overwriting the 127.0.1.1 set up by network-manager's dnsmasq.

Editing resolv.conf to 127.0.1.1 lets domains resolve. Editing to 192.168.0.1 results in connection refused (which is good, I only want to run it as a local cache).

There must be a config option I'm missing as apparently it's supposed to work. See #104: [https://bugs.launchpad.net/ubuntu/precise/+source/djbdns/+bug/959037](https://bugs.launchpad.net/ubuntu/precise/+source/djbdns/+bug/959037)

---

### Post by dino99 on 2012-08-23
i've fallen in trouble today also: was working normally then without major upgrades, i've fully lost internet connection, even ping was failing.

so i've deactivated dns=dnsmasq into nm conf and set a static dns-nameserver into the interfaces.

Then internet is back again.

---

### Post by jfernyhough on 2012-08-23
Solution!

The change to the network-manager copy of dnsmasq to 127.0.1.1 means real dnsmasq can listen on **lo** (i.e. 127.0.0.1). Old configuration file prevented dnsmasq from running on lo. Gah. So the real (caching!) dnsmasq wasn't doing my lookup requests for how long?

$ sudo nano /etc/dnsmasq.d/network-manager

comment out the line:
# except-interface=lo

Restart dnsmasq and network-manager:
$ sudo service network-manager restart
$ sudo service dnsmasq restart

And now my virtual machines can again do DNS lookup over NAT! Hooray!

```
$ sudo netstat -nl46p | grep :53
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      26965/dnsmasq   
tcp        0      0 192.168.0.52:53         0.0.0.0:*               LISTEN      26965/dnsmasq   
tcp        0      0 192.168.0.85:53         0.0.0.0:*               LISTEN      26965/dnsmasq   
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      19580/dnsmasq   
tcp6       0      0 ::1:53                  :::*                    LISTEN      26965/dnsmasq   
tcp6       0      0 fe80::226:b9ff:fec1::53 :::*                    LISTEN      26965/dnsmasq   
tcp6       0      0 fe80::221:6aff:fea3::53 :::*                    LISTEN      26965/dnsmasq   
udp        0      0 127.0.0.1:53            0.0.0.0:*                           26965/dnsmasq   
udp        0      0 192.168.0.52:53         0.0.0.0:*                           26965/dnsmasq   
udp        0      0 192.168.0.85:53         0.0.0.0:*                           26965/dnsmasq   
udp        0      0 127.0.1.1:53            0.0.0.0:*                           19580/dnsmasq   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1891/avahi-daemon: 
udp6       0      0 ::1:53                  :::*                                26965/dnsmasq   
udp6       0      0 fe80::226:b9ff:fec1::53 :::*                                26965/dnsmasq   
udp6       0      0 fe80::221:6aff:fea3::53 :::*                                26965/dnsmasq   
udp6       0      0 :::5353                 :::*                                1891/avahi-daemon: 
```

---

### Post by dino99 on 2012-08-23
Good catch, thanks ):P

---

