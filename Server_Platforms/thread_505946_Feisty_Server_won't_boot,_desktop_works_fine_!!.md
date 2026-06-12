---
title: "Feisty Server won't boot, desktop works fine !!"
date: 2007-07-20
forum: Server Platforms
---

### Post by TrevorNC on 2007-07-20
Hopefully someone can help because I am running out of ideas. I have opened a bug [https://bugs.launchpad.net/ubuntu/+bug/127097](https://bugs.launchpad.net/ubuntu/+bug/127097) on this problem but was hoping that someone may have some suggestions to get me moving forward.

I am trying to set up a server and installed the server version of Feisty. The install worked fine, however after grub runs, I see "Starting up ...." on the screen and then the machine reboots. This sequence of events will continuously loop. Recovery mode does not work either !!

I then installed the Desktop version by running the live CD and clicking on the Install icon. This installed fine and also booted fine too !!

I have checked the grub files and they looked good.

What could be causing the server to fail but the desktop to work ? Could it be something in the initrd.img file that's different and causing the problem ?

Thanks in advance,
Trevor

---

### Post by HermanAB on 2007-07-20
No idea, but there is nothing wrong with running a desktop version for a server.  If you really want to release every last ounce of memory just log out.  The scheduler and memory manager will take care of things.  Stuff that do nothing will eventually get swapped out.

Cheers,

Herman

---

