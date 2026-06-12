---
title: "Network Bridge Freezing"
date: 2018-05-27
forum: Virtualisation
---

### Post by moffa on 2018-05-27
Over the past couple days, the network on the VM's keeps locking up every 10 seconds.  On the host machine under dmesg I see multiple messages like[ 6824.854199] br0: port 3(tap1) entered disabled state

```

[ 6824.854592] device tap1 left promiscuous mode
[ 6824.854595] br0: port 3(tap1) entered disabled state
[ 6825.164213] br0: port 2(tap0) entered blocking state
[ 6825.164214] br0: port 2(tap0) entered disabled state
[ 6825.164271] device tap0 entered promiscuous mode
[ 6825.164292] br0: port 2(tap0) entered blocking state
[ 6825.164293] br0: port 2(tap0) entered listening state
[ 6825.167263] br0: port 3(tap1) entered blocking state
[ 6825.167265] br0: port 3(tap1) entered disabled state

```

I've tried recompiling qemu, running an older kernel, but nothing seems to work. I have no idea how to troubleshoot this.


--edit-- apparently systemd all of a sudden was restart the service.. no idea why

---

### Post by KillerKelvUK on 2018-05-28
Have you got an L2 switching loop in your setup?  Those logouts I believe are the Spanning Tree Protocol activities on your bridge, if your are confident you do not have any L2 loops you can disable STP on linux-bridges.

EDIT:  Sorry just seen the post was marked solved after I posted a reply

---

