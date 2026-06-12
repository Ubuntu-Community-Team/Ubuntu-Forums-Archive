---
title: "Switching from Win server to Linux but want to keep GUI"
date: 2011-09-14
forum: Server Platforms
---

### Post by Jettbot on 2011-09-14
Currently have a windows server file sharing to a bunch of windows workstations but as it has 8 cores (16 multi-threaded) we sometimes use some of the cores for rendering/CG simulations and many of those apps run in the GUI besides all those cores are over kill for just simple file sharing (we do keep at least 2 cores dedicated to file serving and check RAM usage constantly)

But I'd like to switch to Linux so I can add iSCSI (with dedupe) or AOE sharing of boot disks to the Win 7 workstations plus a bunch of other cool things I want to do in Linux. Would love to also explore fibre-channel and cluster aware filesystems as we build a DIY SAN soon (if I can figure out how Win 7 clients can access that filesystem).

But I need to keep the GUI for some apps. However I'm hesitant to install the desktop version of Ubuntu as I really don't need most of that extra stuff. I'd like to keep Unity though if possible for the few times I need to run some stuff in the GUI especially when I need Win apps under VMware.

I've read posts from users wanting Ubuntu server + desktop for similar reasons to mine but they are for older version of Ubuntu prior to Unity.

What's the best way to get 11.04 server going with an automatic Unity login?

Anything else I should know before I blow up my Windows partition and am offline for a few hours?

Thanks!

---

### Post by tgm4883 on 2011-09-14
> **Jettbot said:**
> Currently have a windows server file sharing to a bunch of windows workstations but as it has 8 cores (16 multi-threaded) we sometimes use some of the cores for rendering/CG simulations and many of those apps run in the GUI besides all those cores are over kill for just simple file sharing (we do keep at least 2 cores dedicated to file serving and check RAM usage constantly)

But I'd like to switch to Linux so I can add iSCSI (with dedupe) or AOE sharing of boot disks to the Win 7 workstations plus a bunch of other cool things I want to do in Linux. Would love to also explore fibre-channel and cluster aware filesystems as we build a DIY SAN soon (if I can figure out how Win 7 clients can access that filesystem).

But I need to keep the GUI for some apps. However I'm hesitant to install the desktop version of Ubuntu as I really don't need most of that extra stuff. I'd like to keep Unity though if possible for the few times I need to run some stuff in the GUI especially when I need Win apps under VMware.

I've read posts from users wanting Ubuntu server + desktop for similar reasons to mine but they are for older version of Ubuntu prior to Unity.

What's the best way to get 11.04 server going with an **automatic Unity login**?

Anything else I should know before I blow up my Windows partition and am offline for a few hours?

Thanks!

A server with an automatic login? That just seems like a bad idea.

---

### Post by arrrghhh on 2011-09-14
> **tgm4883 said:**
> A server with an automatic login? That just seems like a bad idea.

Indeed.

Either way to the OP - if you want Ubuntu Desktop, install Ubuntu Desktop.  The Server Edition is meant to be lean and mean - which you don't care about.  So don't try to fit a square peg into a round hole... Just go for the Desktop Edition.  You'll save yourself a lot of time and headache down the road - plus, it can run all the same services the Server Edition can.

---

### Post by kagz on 2011-09-14
First ubuntu is a good o.s and would recommend it 2 u if u want to go linux..u can install the gnome desktop if u need a gui for ur server...welcome to unity..
use:
 sudo apt-get install ubuntu-desktop

---

### Post by arrrghhh on 2011-09-14
> **kagz said:**
> First ubuntu is a good o.s and would recommend it 2 u if u want to go linux..u can install the gnome desktop if u need a gui for ur server...welcome to unity..
use:
 sudo apt-get install ubuntu-desktop

Please, PLEASE don't do this on a server.  You are much better off just installing Ubuntu Desktop... seriously.  **Don't do this!!!**

---

### Post by kagz on 2011-09-14
> **arrrghhh said:**
> Please, PLEASE don't do this on a server.  You are much better off just installing Ubuntu Desktop... seriously.  **Don't do this!!!**

if ubuntu desktop can do what you require i would advice you follow **arrrghhh**'s advice

---

