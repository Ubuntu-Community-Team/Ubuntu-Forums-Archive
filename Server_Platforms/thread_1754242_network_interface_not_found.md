---
title: "network interface not found"
date: 2011-05-09
forum: Server Platforms
---

### Post by davidtlc on 2011-05-09
Alright, here's the problem: I have a server going that was running 10.10, then upgraded to 11.04 with no problems, but when I reinstalled 9.04 (so i could muck around with GNUPanel), the install couldn't find the ethernet on the motherboard (which I had no problems with on 10.10 or 11.04).

I'm a bit of a newb, but it seems to me that something is very wrong here because I can't get online. All of the other computers in my house are unaffected, so I think I can narrow it down to the device not being recognized, but beyond that, I'm lost.

Any help is appreciated,

David

---

### Post by rubylaser on 2011-05-10
What does this show?
```
lspci | grep Ethernet
```

And what's in these two files?
```
cat /etc/network/interfaces
```
```
cat /etc/udev/rules.d/70-persistent-net.rules
```

If it's new hardware, there's a possibility that the older kernel in 9.04 doesn't contain the necessary kernel module to recognize your NIC.

---

### Post by volkswagner on 2011-05-10
Most likely your card does not have drivers in 9.04 version.

```
lspci | grep Network
```
or
```
lspci | grep Ethernet
```

You can check log files to see what is going on.

```
less /var/log/dmesg
```

To search for text using less just start your string with '/' without quotes.  To quit less just type 'q'.

You may be able to get the card working if you can locate drivers for it.

As far as using GNUpanel, have you tried to install it on 10.04?  It seems as though support has dropped on the project.  The latest download is from Dec2009.  On the forums it seems just spam bots are getting activity.  I suspect if you do get it running, you'll be on your own if there are issues.

You may be better off with a more recent version of Ubuntu like 10.04 supporting your card and a long term support release.  Then search for an alternate hosting control panel such as [ispconfig3]("http://www.ispconfig.org/ispconfig-3/").

---

### Post by cavalier911 on 2011-05-10
Post output from terminal commands:
```
lspci -nn | grep -i net
```
```
lshw -C network
```

---

