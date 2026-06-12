---
title: "Localhost in gdm chooser list"
date: 2009-02-09
forum: Server Platforms
---

### Post by neca on 2009-02-09
Hi,

I have a powerful server running hoary with X and GDM, and a small old PC running exactly the same.

The server is not running all the times.

What I'm trying to do is :
- when booting small_pc, it runs GDM in chooser mode, tries to detect if big_pc is up. If yes, big_pc appears in the chooser list and from here I can reach the GDM of the big_pc via xdmcp
- when booting small_pc, it runs GDM in chooser mode, and if is sees no one else, it just shows its own GDM.

First part is already solved, the correct options have been put in /etc/gdm/gdm.conf-custom.
Second part seems not easy, or at least requires scripting, but I'd rather keep using mainstream scripts and packages.

So my workaround would be this simple fact :
- when booting small_pc, its gdm_chooser could show every xdmcp server of the network, INCLUDING LOCALHOST !

In a doc, I saw this was possible with xdm, but not full sure.
I'd like to know if this is possible with gdm.

I tried to specify 127.0.0.1 in the list of hosts that have to appear in the chooser, before the broadcast request, but it doesn't show.

Has anyone any advice?

---

### Post by neca on 2009-02-09
Ok, calm down, super cool, I'm answering my own post, let's keep it anyway for further ubuntu xdmcp users :

Just (slap me please) add in /etc/gdm/gdm.conf-custom in the [xdmcp] section :
Enable=true

My local chooser shows now localhost in the list.

---

