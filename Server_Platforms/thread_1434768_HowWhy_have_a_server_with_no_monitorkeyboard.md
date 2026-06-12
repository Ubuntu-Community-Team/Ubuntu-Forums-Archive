---
title: "How/Why have a server with no monitor/keyboard?"
date: 2010-03-20
forum: Server Platforms
---

### Post by Lucky. on 2010-03-20
I know the obvious answer:  SSH / Remote Desktop.  And my company only has three servers, but bear with me...

Both at my job and home though, every once in a while we run into certain anomalies, like so:

1.  The server is so old that it won't boot/reboot without a keyboard/monitor (regardless of the BIOS settings).

2.  Something fails on the server and/or network, so you can't access a server remotely.

Both of these scenarios generally involve downtime, and a lot shorter downtime if you can just get to the machine.

One of my IT specialists was gung-ho on remote access, and disconnected the monitors/keyboards from some servers.  I was irate when a server went down and the company was waiting on him while he wasted an extra 10 minutes setting everything back up to begin troubleshooting.

I'm a big fan of using a KVM, but I don't know if that's practical at businesses with rows and rows of server racks.  One KVM per rack?  What do the big dogs use for solutions like this?

---

### Post by jrssystemsnet on 2010-03-20
> **Lucky. said:**
> What do the big dogs use for solutions like this?1. if a server goes down often enough that this is a big deal... they replace it
2. "crash carts" with monitor/mouse/keyboard on a rolling cart, trundle it right up to the rack in question, plug it in and rock and roll.  if it's a big enough org, the crash cart might also have a KVM-over-IP on it, so that it gets plugged into the machine with the problem, but the machine with the problem then still gets controlled over the network - the admin remotes into the KVM-over-IP, which itself is connected directly to the K, V, M ports on the server.

---

### Post by Ryan Dwyer on 2010-03-20
I think they have them unplugged, but they have a monitor/keyboard that can slide along the rack and they can plug in to any server within a few seconds.

---

### Post by volkswagner on 2010-03-20
I may be way off, but don't some admins still attach via null modem/serial cable to get into console when necessary?

My response to the OP...When you have a room filled with servers that have uptimes measured in months to years, having monitor, kybd, laying around for each is not practical nor efficient.

For the average home user, I think some situations it is just not practical to hang a monitor and keyboard, since often the location is out of the way in a closet, garage, or attic(ouch high heat).  In these cases, sometimes it is more practical to bring the server to the monitor...after a major crash or for maintenance.

For the old machines look into no F1.com.  It is designed for HP/compaq and proprietary....but it allowed me to set my ipaq desktop (oxy moron?) with a LAN cable and power cord, the way a server should be connected.

---

### Post by Lucky. on 2010-03-21
Thanks for the input everyone!  I am enlightened.

---

### Post by PilotJLR on 2010-03-21
Major server brands also have out of band management cards. With HP, it's called iLO, and with IBM it's called RSA.

In both cases, you attach a network cable to the management card, which basically gives you KVM over IP functionality. Provided the network is up, your guys can then VPN in and remotely reboot a machinem or get a VGA connection to it to see the BSoD, etc.

If you have a HP or IBM servers now, you probably already have this (all but the lowest end models include this now), though you may need to buy an "Advanced" license to use the KVM over IP functionality. Without this license, they are still useful to remotely reboot a frozen machine.

---

### Post by jflaker on 2010-03-21
several reasons....if there is one server, you will likely see a "head" on the server (head is a keyboard, monitor and mouse if gui is installed)

headless servers save space and since it is rare to be in front of a server for management, it isn't needed.  as someone mentioned, a crash cart with kb, vid, mouse is often used when necessary.

Today, with virtualization, you can only see the host and not the Virtual Machines running on the host, so a kvm is useless here.

---

