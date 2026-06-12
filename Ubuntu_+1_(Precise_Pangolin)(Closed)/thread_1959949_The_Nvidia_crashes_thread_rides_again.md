---
title: "The Nvidia crashes thread rides again"
date: 2012-04-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by shadowfirebird on 2012-04-16
It's very simple really.

This thread is for anyone who is experiencing -- as I am -- random kernel hangs (that means the whole computer freezes and your keyboard lights blink) and X crashes (that means you get logged out without warning).  If you are having the same symptoms you can talk about them here.  

If, on the other hand, you are just recently getting really slow graphics, then you should go [here]("http://ubuntuforums.org/showthread.php?t=1959416").  **Having slow graphics is not the same thing as having crashes.**  My Kernel crashes may have nothing to do with Nvidia, in fact, AFAIK.  

So don't go [here]("http://ubuntuforums.org/showthread.php?t=1959416") to talk about crashes.  Except that my original thread on crashes was moved there and apparently can't be moved back, so **DO** go there to read the original conversation about crashes.  And then come back here.

Clear?


To make things as easy as possible for people, I'll try and summarise:

* I've had it since the -20 kernel, currently on the -23 one.

* It may be [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/978342") bug.

* Here is a section of my kern.log file after a kernel crash:
```

Apr 16 12:22:10 blake kernel: [11127.936825] sd 4:0:0:0: [sdb] 31116288 512-byte logical blocks: (15.9 GB/14.8 GiB)
Apr 16 12:22:10 blake kernel: [11127.938812] sd 4:0:0:0: [sdb] No Caching mode page present
Apr 16 12:22:10 blake kernel: [11127.938824] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Apr 16 12:22:10 blake kernel: [11127.942811] sd 4:0:0:0: [sdb] No Caching mode page present
Apr 16 12:22:10 blake kernel: [11127.942822] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Apr 16 12:22:10 blake kernel: [11127.947834]  sdb: sdb1
Apr 16 12:39:12 blake kernel: [12149.628762] **NVRM: GPU at 0000:02:00.0 has fallen off the bus.**
Apr 16 12:39:12 blake kernel: [12149.628771] NVRM: os_pci_init_handle: invalid context!
Apr 16 12:39:12 blake kernel: [12149.628773] NVRM: os_pci_init_handle: invalid context!
```

* Here is a section of my syslog following an X crash:
```
Apr 16 15:29:33 blake kernel: [ 6987.760289] NVRM: Xid (0000:02:00): 6, PE0001 
Apr 16 15:29:33 blake gnome-session[4862]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.#012
Apr 16 15:29:34 blake acpid: client 4653[0:0] has disconnected
Apr 16 15:29:34 blake acpid: client 4653[0:0] has disconnected
Apr 16 15:29:34 blake acpid: client connected from 5771[0:0]
Apr 16 15:29:34 blake acpid: 1 client rule loaded
Apr 16 15:29:34 blake acpid: client connected from 5771[0:0]
Apr 16 15:29:34 blake acpid: 1 client rule loaded
```

* I see two nvidia drivers, a recommended one and a later one.  It definitely seems a little better on the later one -- say, one to three crashes a day.  

Currently trying Ubuntu 2D (which I can't live with in real life) to see if that effects anything.

All help greatfully appreciated.

[B]
Update[/B]: Just to make things even more simple, one of the other people having this trouble has also restarted the thread, [here]("http://ubuntuforums.org/showthread.php?p=11849075").

---

