---
title: "Firefly (mt-daapd) crashing on startup"
date: 2009-05-04
forum: Ubuntu Studio
---

### Post by Missionary Man on 2009-05-04
I'm running 8.04 on a headless server with Firefly (mt-daapd) serving my iTunes library to 2 Roku Soundbridges.

All worked fine for a long time, but recently, mt-daapd crashes on startup. Here's the logfile:

```
2009-05-04 12:14:21 (b74fb6c0): Firefly Version svn-1696: Starting with debuglevel 5
2009-05-04 12:14:21 (b74fb6c0): Loaded plugin /usr/lib/mt-daapd/plugins/rsp.so (rsp/svn-1696)
2009-05-04 12:14:21 (b74fb6c0): Loaded plugin /usr/lib/mt-daapd/plugins/out-daap.so (daap/svn-1696)
2009-05-04 12:14:21 (b74fb6c0): No ssc program specified for script transcoder.
2009-05-04 12:14:21 (b74fb6c0): Error loading plugin /usr/lib/mt-daapd/plugins/ssc-script.so: plugin declined to load
2009-05-04 12:14:21 (b74fb6c0): Loaded plugin /usr/lib/mt-daapd/plugins/ssc-ffmpeg.so (ssc-ffmpeg/svn-1696)
2009-05-04 12:14:21 (b74fb6c0): Plugin loaded: ssc-ffmpeg/svn-1696
2009-05-04 12:14:21 (b74fb6c0): Plugin loaded: daap/svn-1696
2009-05-04 12:14:21 (b74fb6c0): Plugin loaded: rsp/svn-1696
2009-05-04 12:14:21 (b74fb6c0): Starting rendezvous daemon
2009-05-04 12:14:21 (b74fb6c0): Starting signal handler
2009-05-04 12:14:21 (b74fb6c0): Initializing database
2009-05-04 12:14:21 (b74fb6c0): Query: vacuum
2009-05-04 12:14:21 (b74fb6c0): Error: constraint failed
2009-05-04 12:14:21: Aborting
2009-05-04 12:14:21 (b6ca9b90): Rendezvous socket closed (daap server crashed?)  Aborting.
2009-05-04 12:14:21: Aborting

```

Can anyone help or advise?

---

### Post by neonleonb on 2009-05-12
Yeah, apparently there's a bug ([https://bugs.launchpad.net/ubuntu/+source/mt-daapd/+bug/343069](https://bugs.launchpad.net/ubuntu/+source/mt-daapd/+bug/343069)). See that link for a patch and instructions on how to use it. I don't know when they'll release a fixed package, but I hope it's soon.

---

