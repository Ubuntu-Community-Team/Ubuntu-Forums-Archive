---
title: "kvm eats 100% processor, Hardy64, amd x2 5600"
date: 2008-04-28
forum: Virtualisation
---

### Post by reference2myself on 2008-04-28
KVM eats 100% of my processor on Hardy 64 bit.  I have an amd athlon 5600 with virtualization turned on in the bios.  Everything runs fine, my computer responds like all of the processing power is still available, kvm just eats up whatever isn't being used by anything else.  Is anyone else experiencing this, any ideas?

---

### Post by Red Shift on 2008-04-28
You're using VirtualBox, yes?

I had a similar experience installing 8.04 as a guest on a 7.04 64-bit host.  IIRC, as this was two days ago, I solved the problem by logging out (not shutting down) and logging back in.  I may have also installed Guest Additions during that time.

---

### Post by reference2myself on 2008-04-28
Sorry, I should have provided more info.  I'm using virt-manager and I'm trying to use Windows XP MCE 2005.

---

### Post by alexsabree on 2008-04-29
I've heard a lot about this problem. I don't recall the exact reason why this happens, but for some reason the word "overhead" comes to mind.. :(

As long as you don't think that its slowing you down, i wouldn't worry.

---

### Post by reference2myself on 2008-04-29
It doesn't seem to be slowing me down but it's making my cpu cores rise from 28 degrees up to 50!!  I just tried it out with vista and it works just fine.  I tried a few different versions of xp, all with the same result, it seems the problem is xp specific.  I need the windows media center to stream videos to my xbox 360 and vista is too slow.  I might have to go back to using vmware, I really wanted to get it working with virt-manager and kvm though.

---

### Post by reference2myself on 2008-05-05
I have narrowed down this problem to be strictly with Windows XP when using more than 1 virtual processor.  If I set it up with 1 processor it's fine, with 2 processors it eats up both my cores.  It doesn't happen with Vista.  Is anyone else experiencing this, maybe I should report it as a bug?  I have my media streaming set up for my 360 now but it's not fast enough to transcode high def x264 in real time, I need both cores going to work like I had it in VMWare.

---

### Post by agent8131 on 2008-05-06
You should report it as a bug.  There may be a way to resolve it, but then again there may not be at this time.

---

### Post by reference2myself on 2008-05-08
I reported this as a bug, [Bug #228442]("https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/228442")

---

### Post by graylion on 2009-02-09
getting the same with intrepid guest and intrepid host, both amd64

---

