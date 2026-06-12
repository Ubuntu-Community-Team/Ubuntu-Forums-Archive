---
title: "ZFS stuck on import"
date: 2020-08-02
forum: Server Platforms
---

### Post by arneklaver on 2020-08-02
Hello,

I'm having some trouble importing my zfs pool to a new machine.

[B]short:
[/B]When I try to import my pool (zpool import) the command hangs and I can not execute any more zfs commands. (tested on: freenas,ubuntu,debian)

**Long:**
Previously I was running Xen server with a FreeNAS VM, but now I'm trying to switch to another machine and run my ZFS pool on Ubuntu (no VM).

Before I tried to switch to ubuntu I already ran into some problems. So one of my drives broke down and I did the re silvering everything went fine except that I had some data los I believe because I did not do regular scrubs (very dumb of me) but nothing important was lost. after the re silvering I had a zpool status of degraded and every time I did a reboot it started the re silvering again.
to fix this and get my pool in an ok state I tried doing a zpool clean, but this command froze and I could no longer acces any of my data? Here I got a bit scared but after a reboot and after it did the re silvering again. I did a scrub first and then a clean and everything was fine and my pool was in a online state no errors.

At this point I decided to do an export and try to import the pool on a new machine. but every time I try to import the command freezes and I can not execute any more zfs commands. (tested on: freenas,ubuntu,debian)

When I look in ubuntu dmesg it tels me bad RIP value. and that the proces has been stuck for ... seconds.

If you need any more info feel free to ask, I wil try to be as precise as I can.
Regards,
Arne

---

### Post by arneklaver on 2020-08-04
Is there a forum that might be better suited for this zfs questions?

---

### Post by arneklaver on 2020-08-09
So thank you very much for the answers.
If anyone is facing similar issues you can import your pool in read only mode to recover some (probably not all) of your data.
# **zpool import -o readonly=on tank**
[B]Other than this I did not find a solution and I'm going to create a new pool.

[/B]

---

### Post by ameinild on 2020-09-13
Hi. Sorry to hear you didn't fully solve the issue. For future reference, the forum [https://unix.stackexchange.com](https://unix.stackexchange.com) might be a place to get more technical answers regarding ZFS. I would actually personally prefer that over [https://askubuntu.com/](https://askubuntu.com/) which is also on Stack Exchange, but Ubuntu specific.

---

