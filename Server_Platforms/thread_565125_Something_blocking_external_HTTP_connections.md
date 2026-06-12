---
title: "Something blocking external HTTP connections?"
date: 2007-10-01
forum: Server Platforms
---

### Post by antisho on 2007-10-01
My computer is not accepting port 80 connections from outside the local network. I've looked at some other threads, but none of them match my circumstances exactly.

I know it worked before, as recently as a few weeks, and I'm reasonably sure I haven't changed any firewall settings or anything since then. I doubt it's an ISP-blocking-port-80 problem because ports 81 and 8080 don't work either. I have a static IP and everything is fine when I access it through that IP, but when I try the network's IP, it doesn't load and times out. If I turn off the router's port 80 forwarding, I get the router page, so stuff is getting through. If I go through port 8080 when port 8080 forwarding isn't enabled, I get and immediate cannot-connect error.

My best thought at this point is that something else is blocking external packets. This is evidenced by the fact that if I redirect port 80 packets to another machine on the network, it loads fine, and SSH connections to this one are blocked as well. However, I have no idea what's doing it or how to stop it. Can anyone help?

---

### Post by p_quarles on 2007-10-01
So, you get the router's config page using the external IP address of the LAN address? If the latter only, I'd say it's certainly possible that the ISP is blocking traffic. 

Also, when you are changing ports on the router, are you also reconfiguring Apache to listen on that port? 

This may not be helpful, since this does indeed sound like a strange situation, but I thought I'd give it a shot.

---

### Post by HermanAB on 2007-10-02
Here are some basic tips.

Display the netfilter rules with:
$ sudo iptables -L

Flush all rules with:
$ sudo iptables -F

Check the tcpwrappers settings in /etc/hosts.allow and allow everything with:
ALL:   ALL

Test connectivity with a simple tool:
$ telnet localhost 80
$ telnet public.ip.addr.ess 80

Cheers,

Herman

---

### Post by p_quarles on 2007-10-02
If iptables were blocking the relevant port, it wouldn't be available to the LAN, so I really doubt that's the problem.

---

### Post by antisho on 2007-10-02
> **p_quarles said:**
> So, you get the router's config page using the external IP address of the LAN address? If the latter only, I'd say it's certainly possible that the ISP is blocking traffic. 

Also, when you are changing ports on the router, are you also reconfiguring Apache to listen on that port?
Yes, I get the router's config page from the outside, if forwarding is off, and from inside.

I edited ports.conf and added a Listen 8080, but it still didn't work.

iptables didn't fix it; telnet couldn't connect.

---

### Post by p_quarles on 2007-10-02
> **antisho said:**
> Yes, I get the router's config page from the outside, if forwarding is off, and from inside.

I edited ports.conf and added a Listen 8080, but it still didn't work.

iptables didn't fix it; telnet couldn't connect.
Very strange. All I can think of is adding the LAN IP address to the listening port (if you haven't already), e.g.:
```
Listen 192.168.0.10:8080
```
That's the "correct" way to do it, although in my experience it's not strictly necessary. Could help, though.

---

### Post by antisho on 2007-10-02
All right, this is rather strange. I took your suggestion, p_quarles. Then... I think part of the problem was Firestarter, which I didn't even know was *running*, because there's never an icon in the notification area until I actually run System>Administration>Firestarter. Also, I didn't remember having previous problems with Firestarter. But I turned it off, and it worked... for a minute. At least, it showed the front page of my server, but nothing else would load.

The nothing-loading part was after I
1) Uninstalled Firestarter instead of just turning off the firewall, and
2) Removed the IPs from ports.conf to see if it mattered, but I changed it back, so I don't see how it would affect anything.
Right now, everything's working, but I have no idea why...

---

