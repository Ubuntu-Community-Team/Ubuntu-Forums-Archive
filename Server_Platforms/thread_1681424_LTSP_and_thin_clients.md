---
title: "LTSP and thin clients"
date: 2011-02-04
forum: Server Platforms
---

### Post by spynappels on 2011-02-04
I'm looking at setting up my own LTSP server and have been looking at various thin clients on ebay. I'mjust not sure whether some specific ones will work and the tech support for them seems to be limited.

Does anyone have any experience with NComputing? I don't think that will do what I want because all their literature talks about their own proprietary software suite.

What about Wyse Thin Clients? I know they are a big player, but I'm not sure whether they have PXE boot capability.

Any body care to enlighten me?

---

### Post by gottr on 2011-02-10
Do you have an old PC or laptop that you could use as a thin client?  I have been using old Dell models, GX270 and D810, as thin clients to much success.  Sorry but I have not direct experience with "actual" thin clients.

---

### Post by Roasted on 2011-03-08
We have NComputing at the moment. I think we are stretching the usage quite thin, however we have a powerhouse server.

Two Quad Core Processors
32gb RAM
4 Gigabit ethernet ports dedicated entirely to 30 NComputing clients.

They suck. The server must be rebooted daily for all of them to wake up and realize the connection is available.

As a result, I'm beginning to wonder if it's worth mentioning LTSP to the bossman. I'm going to set up a test environment tomorrow to see how it goes. I asked some RevolutionLinux employees earlier if NComputing was compatible with LTSP and they said no, as the thin client boxes must retain capability of being able to boot a Linux kernel. Since NComputing boxes are essentially dumb clients (no helper processor, very limited without their parent server) they are unable to be supported with it.

Sorry I can't offer much more. I hope this helps though.

---

### Post by MikeUK on 2011-03-16
I've used mainly Neoware units, I find I have issues with Ubuntu and the older EON models with the 300mhz CPU's, but they will run smaller OS's such as tiny core

However I find that the Neoware CA2's work very well (800mhz CPU's), although the savage video isn't that great, It all depend on how hard you want them to work.

---

### Post by LS1987 on 2011-03-17
Does LTSP thin client (version < 5) run on Pentium I with 32 MB RAM with accettable performance?
I specified version < 5, because version 5 requires a Pentium II (architecture 686+).

---

