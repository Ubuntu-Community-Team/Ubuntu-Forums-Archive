---
title: "Jack problems registering firewire device ports"
date: 2012-11-29
forum: Ubuntu Studio
---

### Post by TheFisherman on 2012-11-29
Hi there,

just installed KXStudio atop my Ubuntustudio 12.04 installation. Cadence is a quite comfortable tool.
Problem is, since the installation jack has problems registering the ports of my Echo Audiofire 4 firewire device:

```
ERROR: firewire MSG: Streaming thread running with Realtime scheduling, priority 93
ERROR: firewire MSG: Registering audio capture port firewire_pcm:001486ef9f398a52_Unknown_in
...
(same with the other ports)
...
ERROR: port_name "firewire_pcm:001486ef9f398a52_Unknown_in" already exists
ERROR: driver: cannot register port for firewire_pcm:001486ef9f398a52_Unknown_in
ERROR: Cannot attach audio driver
...
ERROR: JackServer::Open failed with -1
...
ERROR: Failed to open server
ERROR: Segmentation Fault!
...

```

I have not the faintest idea where this comes from. Perhaps the realtime scheduling is the clue?

---

