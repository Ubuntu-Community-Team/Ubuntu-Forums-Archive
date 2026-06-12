---
title: "Checkpoint VPN"
date: 2007-08-05
forum: Server Platforms
---

### Post by grahams on 2007-08-05
Does anyone know if it is possible to connect to a Checkpoint VPN server and if so which client is recommended. I've used vpnc to successfully connect to my current company's Cisco VPN, but I'm starting a new job next month and they use Checkpoint and told me there is no Linux client support. From scanning Checkpoint's website it look like they had a client for the 2.4 kernel but dropped support for it. 

I'm moving to a small company and I may be able to convince them to move to an open VPN solution. Any recommendations?

---

### Post by grahams on 2007-08-24
bump

---

### Post by eentonig on 2007-08-24
I'm in the same situation. Never found a solution.

---

### Post by grahams on 2007-10-17
Only solution I found was to convince our IT guys to dump Checkpoint, which they did :) Viva openVPN

---

### Post by netlogic on 2007-10-19
It doesn't exist from what i know. that's what happens when greedy companies try to lock you in with the upgrades.

---

### Post by selectron on 2007-10-19
Hi all!  :)
I have began hacking openswan and found out follow...
[http://wiki.openswan.org/index.php/Interop/InteroperatingCheckpoint](http://wiki.openswan.org/index.php/Interop/InteroperatingCheckpoint)
but I didn't test those recomendations.
If you find out this useful, please, write in this topic.

---

### Post by trondhuso on 2008-02-20
Couldn't really figure anything out following those links, but back in 1999 the company supported Linux: [http://www.checkpoint.com/press/1999/linux111699.html](http://www.checkpoint.com/press/1999/linux111699.html)

Should one go and ask them to support Ubuntu in the future? 

Anyway: Has anyone solved the problem on connecting with VPN to a CheckPoint VPN Server?

---

### Post by ekravche on 2008-04-13
Haven't got it working successfully with Checkpoint. Here is another thread in which you can read about some helpful suggestions [http://ubuntuforums.org/showthread.php?t=340307](http://ubuntuforums.org/showthread.php?t=340307)

---

