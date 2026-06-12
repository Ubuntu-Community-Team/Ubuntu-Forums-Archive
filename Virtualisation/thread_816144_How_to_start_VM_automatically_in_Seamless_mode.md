---
title: "How to start VM automatically in Seamless mode"
date: 2008-06-02
forum: Virtualisation
---

### Post by sox on 2008-06-02
Good morning.

I use VirtualBox (1.6 v) on my Hardy Heron.
I would like to know if it is possible to start a Virtual Machine (XP) automatically in "seamless mode".
Yes I know there is the "control dx + L" option...

I've checked on VBoxManage options, but I've not found any options.

Thanks
Luca

---

### Post by HermanAB on 2008-06-02
I simply run the VM and connect to XP using RDP.

Just plug this into Google "rdesktop seamless rdp" and you shall get links to Cendio and Ubuntu forums.

Cheers,

Herman

---

### Post by sox on 2008-06-03
THanks Herman for your reply.
I've already seen rdesktop with seamless functionality.. and it's very cool.
But I wanna use only VirtualBox.
With HOME + L I run the seamless mode... so I think it's possible to run virtualbox automatically in this mode.

Actually I start Virtualbox automatically with the command: VBoxManage startvm VM-number, and then HOME + L.

Is it possible that there isn't any parameter or something else to enable this feauture automatically?

Thanks.
Luca

---

### Post by starcannon on 2008-06-04
I use the closed source Vbox and it remembers my last session settings, so if I shut windows down while in seamless mode, then when I start it up again it pops up in seamless mode.

I don't know if there is a particular command, but since it appears to remember its last state perhaps just be sure to shut windows down in seamless mode would do the trick?

---

### Post by sox on 2008-06-04
Thank you starcannon for your reply.
This suggestion works even if It can't reach the level of integration with my ubuntu that I want..

---

