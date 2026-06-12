---
title: "No internet on otherwise good wifi connection"
date: 2021-08-27
forum: Ubuntu/Debian BASED
---

### Post by mazate33 on 2021-08-27
Hi there

I installed POPos on an old imac and I'm having an issue (for a 2nd time) where the internet works fine for a few days and then it stops working.  The wifi is connected to the router.  All of the settings are there.  The computer is seen by the router.  Everything looks fine but I can't figure out why I have no internet.  I've tried resetting the router and that doesn't seem to have helped.  I've disconnected the wife and reconnected and that didn't matter either.  When it was working the first few days everything was fine.  Now it still connects to the wifi but no internet.  I even reinstalled the OS and had the same thing.  It worked for a few days and then stopped.   Any help is most appreciated.

---

### Post by TheFu on 2021-08-28
Please post these commands and outputs:

```
ip add
ping -c 3 8.8.8.8
ip route |column -t
more /etc/resolv.conf
```

When posting, wrap the commands and output in a single code-tag, please, so things line up and are readable. Advanced editor (#) button. I used code tags for the commands to run above. Just like using quote tags, just quote --> code instead.

Sometimes a DNS issue looks like a network issue.

---

### Post by mazate33 on 2021-08-28
I'm going to have to figure out a way to copy the content over because that computer has no internet so I don't have a way to copy/paste it.

---

### Post by Frogs Hair on 2021-08-28
Moved to Ubuntu/Debian Based.

---

### Post by TheFu on 2021-08-28
> **mazate33 said:**
> I'm going to have to figure out a way to copy the content over because that computer has no internet so I don't have a way to copy/paste it.

Use either redirection or 'tee'
```
ip add                 | tee    /tmp/mylog
ping -c 3 8.8.8.8      | tee -a /tmp/mylog
ip route |column -t    | tee -a /tmp/mylog
more /etc/resolv.conf  | tee -a /tmp/mylog
```

-a is "append". Don't worry about the exact spacing. I did that to make a point that these lines are VERY similar.

The copy the tmp/mylog file to a flash drive (aka sneaker*net) ... and upload it here, wrap in code tags.  Bob's your uncle.
There are all sorts of this possible with redirection too.  [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)  is a text document that explains lots of simple things every Linux/Unix person should know for being efficient in a shell.  There's a section about redirection.

I would do it a little  different than what I wrote above myself, but whatever works is fine.  Felt that using consistent solution could be helpful rather than showing the efficient methods or having you run a script.  If the ping works, then you just have a DNS problem, not a network problem.

---

### Post by mazate33 on 2021-08-29
```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether c8:2a:14:20:e8:f0 brd ff:ff:ff:ff:ff:ff
3: wlp3s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether e4:ce:8f:52:8c:da brd ff:ff:ff:ff:ff:ff
4: ipv6leakintrf0: <BROADCAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default qlen 1000
    link/ether fa:21:3f:25:f3:41 brd ff:ff:ff:ff:ff:ff
    inet6 fdeb:446c:912d:8da::/64 scope global noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::1172:ca88:b4a2:2d76/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "resolvectl status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs should typically not access this file directly, but only
# through the symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a
# different way, replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.


nameserver 127.0.0.53
options edns0 trust-ad
search .

```

---

### Post by TheFu on 2021-08-29
So, since some of the commands aren't included, and the wifi device doesn't have any settings, looks like the wifi isn't connecting to your wifi AP.

It is NOT a DNS thing (at least not yet).
There is a wireless info script in the "networking" subforum here.  Download that, and run it.
[Https://github.com/UbuntuForums/](Https://github.com/UbuntuForums/) should have it.

Also, if you use a "Try Ubuntu" flash drive (the same as you used to install Ubuntu), does wifi work?

BTW, don't forget that you can probably connect an ethernet cable to the computer and have wired networking work to download the script, run it, and post the results.

---

### Post by mazate33 on 2021-08-29
For what it’s worth it doesn’t work with Ethernet either.

---

### Post by TheFu on 2021-09-17
> **mazate33 said:**
> For what it’s worth it doesn’t work with Ethernet either.

Solved? What did you do?
BTW, did you try booting from an Ubuntu Install flash drive and going into "Try Ubuntu" ... to see if that works fine?  That's an easy way to see if it is a hardware issue or part of the installation that is causing the problem.  You can try a few different Linux distros. Many (most?) desktops have a Try mode these days that will run directly from the ISO file.  xubuntu, lubuntu, ubuntu-mate, Mint, all do.  There's always tinycore too, if you want to use a distro with less than 200MB in size.

---

