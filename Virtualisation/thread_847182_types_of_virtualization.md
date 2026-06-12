---
title: "types of virtualization"
date: 2008-07-02
forum: Virtualisation
---

### Post by andrew_awp on 2008-07-02
Ok, i am trying to consolidate all this information, let me see if i have this straight:

there would be basically 3 kinds of virtualization: total, middle, and para-.
starting at the bottom, or hardware, the optimum would be a hypervisor right on top of the equipment, only just being a traffic cop, but no one seems to really do this, except maybe vmware 3i, and i cant get it to install.
xen is really a linux OS, so the problem here is that you cant run something completely different such as windows right on the hardware, for the simple reason all the hardware, such as mouse,video, audio would have to switch from one to the other, and i dont think anyone has done this yet (i wonder if parallels for mac does this to switch from one to the other?).
the closest solution to that would be para-virtualization, i think, but doesnt it have to be the same type of OS?
so then we get to most virtualization solutions, which abstracts the hardware, only using the cpu extensions for added speed. therefor you cannot use special graphics or audio hardware, so mainly useless for a desktop. this is vmware, qemu, etc.
the 3rd way completely mimicks another computer, necessary if you want to host a completely different system such as amiga,ppc,arm,sparc, etc.

my main concerns are: speed, being able to boot an already installed guest from a physical partition, and the guest being able to use accelerated or special hardware.
i think practically, all are out of luck, especially for instance, running windows from a server to another computer over VNC. the 2nd concern is only going to work if the virtualization host and the physical hardware are seen as the same or close to the same by the guest OS.

---

### Post by HermanAB on 2008-07-02
You analyze too much.  Just go and try it!

If you wish to run Windoze XP only, then use Virtualbox.  If you wish to run anything at all, then use VMware.

You shall be pleasantly surprised by the speed of these systems.

Cheers,

Herman

---

### Post by andrew_awp on 2008-07-02
why do you say vmware runs anything and virtualbox wont? I mean on an x86 or x86-64 processor.

I used to use vmware server on winXP-64, ran 32bit windows as guest (because some apps and drivers dont run on x64). It was a bit slower then native, but then i was using a single sempron processor.

---

### Post by Victormd on 2008-07-02
Virtual box will run pretty much anything too, as long as you use the personal use and evaluation, and not the open source version. As for 3D graphics and other hardware support, you won't get with any virtualization because your virtual machine is simulated as a basic PC and does not incorporate information from your actual HW. However, the speed with which it runs is quite nice.

---

