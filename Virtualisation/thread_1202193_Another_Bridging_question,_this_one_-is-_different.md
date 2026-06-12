---
title: "Another Bridging question, this one -is- different!"
date: 2009-07-02
forum: Virtualisation
---

### Post by mangeek on 2009-07-02
Greetings,
     I'm actually a very experienced Linux user (been using Linux since 1998, when setting up X took hours, and downloading an ISO took days and days).

     I decided to use Ubuntu recently, since it seems well-supported and relatively polished and up-to-date (debian proper moved too slow, gentoo support is like being in a mosh pit).

     What I have is some beefy hardware running Virtualbox, and I'm serving a drive out as an iSCSI target to a file server VM that imports the target as a local disk, this lets me 'snapshot' the state of the system disk of the virtual file server, but not have to snapshot the data it serves (which would lead to giant, slow snapshot files). I also have several other VMs running all sorts of stuff, mostly feeding-off files on served from the 'server' VM.

     The problem I have is that the VMs need to be visible to hosts on the LAN, so I have them set up with Virtualbox's 'Bridged Connection' to eth0. Normally this is not an issue, but both the iSCSI and VM-VM CIFS traffic is traversing the physical wire, making things much slower and incurring much more overhead than they should.

     Since the host is the iSCSI target (read: server), and the VMs are servers and clients, and there are real physical clients on the LAN, what I'd like to do is set up a bridge to keep VM-host and VM-VM traffic -off- the LAN at layer 2 (basically, having an ' ethernet switch' inside my computer.

So I think I have a plan, but I have no idea how to implement it:

I want a bridge (lets call it br0) with eth0 connecting it to the 'outside', and a virtual interface (called v0) that's also connected to the bridge, the VMs and the DHCP client would only run on v0, so traffic that didn't need to leave the bridge would never make it onto a physical wire.

Here's the problem:

```
LAN---switch---host(eth0, 192.168.1.10)
                      |---VM(bridged to eth0, 192.168.1.x)
                      |---VM(bridged to eth0, 192.168.1.x)
                      |---VM(bridged to eth0, 192.168.1.x)
```

And here's my idea for a solution:

```
LAN---switch---host(eth0, no IP)
                      |---br0
                             |---host (v0, 192.168.1.10)
                             |---VM(bridged to br0, 192.168.1.x)
                             |---VM(bridged to br0, 192.168.1.x)
                             |---VM(bridged to br0, 192.168.1.x)
```

   Can anyone tell me how I would go about doing this? It seems a bit more in-depth than the other forum posts I've read up on, especially with the 'no IP on eth0' idea, pushing the host's networking behind a bridge on the host itself.

---

### Post by mangeek on 2009-07-02
ugh. my graphical description didn't quite work out, the formatting got filtered-out. I hope my description is good-enough.

---

### Post by dmizer on 2009-07-02
Actually, I believe there are virutalization-specific techniques to do what you want to do, but I don't know enough about it.

I'm moving this to the virtualization subforum, as I think you'll get more targeted help there.

Edit:
Also added code boxes so your graphical description isn't broken anymore.

---

### Post by mangeek on 2009-07-08
No love? I'm surprised this isn't more of a common issue... I suppose not many people are using Ubuntu and Virtualbox for production-quality serving...

Basically, I really just need to borrow a network-geek's mind for a few minutes.

---

