---
title: "Virtualbox + Allocated Memory"
date: 2008-05-31
forum: Virtualisation
---

### Post by MaindotC on 2008-05-31
When I allocate memory for a virtual machine, that takes from the actual physical memory, correct?  When I turn off the virtual machine, is that memory still held by virtualbox?

I just got a 4GB upgrade for my T60. I'm still having video chop every 5 seconds - nothing really all that bothering but surprising - and it doesn't go full-screen all that cleanly (justin.tv/richsportsonline for example).  I don't wanna delete my vm's and thought I'd ask. I have 1GB allocated for an xp, solaris, and opensolaris vm's.

Reiterating my question, does virtualbox hold onto that memory even after I shut down the vm's and close virtualbox?  Thanks!

---

### Post by Tpolich on 2008-05-31
no, look at the system monitor. When you close Virtualbox or stop the virtual machine you get the ram back.

---

### Post by MaindotC on 2008-06-01
LoL that was stupid of me. I could even look at /proc/meminfo. Thanks for reminding me :)

---

