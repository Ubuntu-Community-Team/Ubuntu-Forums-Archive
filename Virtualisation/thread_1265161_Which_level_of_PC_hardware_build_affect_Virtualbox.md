---
title: "Which level of PC hardware build affect Virtualbox performance ?"
date: 2009-09-13
forum: Virtualisation
---

### Post by ubfu on 2009-09-13
Actually my point is , which PC hardware build perform poorly on VirtualBox ?
Having a AMD x2 2.0ghz and 1GB ram for guest .Having it install with window xp , it seems to run very slow .It support VT but still occupied one of its' core still run very slow.

So , my question , anyone experience upgrade of processor increase the performance for vitualization ? and which hardware part should be upgrade to run smooth ?

Thank you :)

---

### Post by falconindy on 2009-09-13
Keep in mind that VirtualBox itself needs RAM to operate with. Anything you give to the guest OS is in turn taken away from the host. You need to find yourself a happy medium.

That said, I'm currently using a 3.16ghz Core2Duo with 2gb of RAM, and my WinXP install on VBox only uses 256mb of RAM. I will, however, bump this up to 512mb if I'm planning on using VBox for Photoshop. Even with only 256mb devoted, it runs faster than it ever did natively with 2gb. Running with 512mb for photoshop means I have to be careful about how much I leave running back on the host.

---

### Post by Zhwazi on 2009-09-13
A good processor and lots of RAM are the most important things.  Last time I bought a 2GB stick it was $20, and it gives good results.

I have a 2.8GHz Athlon 64 X2 and 6GB of RAM, and running several VM's at once is smooth for guest and host. Make sure you install the guest additions, the mouse integration makes it run smoother.

---

### Post by ubfu on 2009-09-13
> **falconindy said:**
> Keep in mind that VirtualBox itself needs RAM to operate with. Anything you give to the guest OS is in turn taken away from the host. You need to find yourself a happy medium.

That said, I'm currently using a 3.16ghz Core2Duo with 2gb of RAM, and my WinXP install on VBox only uses 256mb of RAM. I will, however, bump this up to 512mb if I'm planning on using VBox for Photoshop. Even with only 256mb devoted, it runs faster than it ever did natively with 2gb. Running with 512mb for photoshop means I have to be careful about how much I leave running back on the host.

As I mention previously I had an AMD x2 2.0GHz.Having an actual 2GB of ram and 1GB are allocated to the guest but I still feel it's slow.Whenever I click an application to load , the cpu always jumps to 100% and I have to wait until it finish loading.Even with browsing getting very slow and lagging behind.( tested with opera , chrome , firefox 3.5) Still the same result.I suspect it's hand of processor.

> **Zhwazi said:**
> A good processor and lots of RAM are the most important things.  Last time I bought a 2GB stick it was $20, and it gives good results.

I have a 2.8GHz Athlon 64 X2 and 6GB of RAM, and running several VM's at once is smooth for guest and host. Make sure you install the guest additions, the mouse integration makes it run smoother.

I am running AMDx2 2.0ghz and 2GB of ram.Did that when I first install the guest.
Which partition you use for the guest and how much of size did you allocated ?

---

### Post by falconindy on 2009-09-13
> **ubfu said:**
> As I mention previously I had an AMD x2 2.0GHz.Having an actual 2GB of ram and 1GB are allocated to the guest but I still feel it's slow.Whenever I click an application to load , the cpu always jumps to 100% and I have to wait until it finish loading.Even with browsing getting very slow and lagging behind.( tested with opera , chrome , firefox 3.5) Still the same result.I suspect it's hand of processor.
Well sure, if your CPU is pegging at 100% then it's clearly choking on cycles. My point, however, was that lowering the amount of RAM you devote to your VirtualBox may actually have a **positive** effect on your overall performance.

---

### Post by ubfu on 2009-09-14
Did that just now setting it to 512mb ram but it just same as 1GB ram allocated.

Would it be the cause of using AMD processor which it run less compatible on virtualbox ?

---

### Post by ubfu on 2009-09-29
I plan to get a Althon x4 620 2.6Ghz.I can't find much on the comparison between Althon x4 620 2.6Ghz and Althon x2 2.1Ghz.
Things that I worry is the performance running virtualbox.Will it still lag and running slow even with 620 2.6Ghz ?

Thank you .

---

### Post by Dedoimedo on 2009-09-29
Disk speed is also important.

Place the virtual machine on a non-system disk, 2nd, usb, etc, and you'll see a marked change in performance and responsiveness.

Cheers,
Dedoimedo

---

### Post by ubfu on 2009-09-30
The problem I am having is everytime I drag a program at the title bar , the cpu usage jump to 100% until I release it.

---

### Post by sabre2th on 2009-09-30
My limited experiences with VirtualBox tell me that I generally wouldn't use it much with less than 4 gigs of RAM and a quad core processor, though I may be slightly more sensitive to slowdowns than some people.

Edit: I also like to have guest OSes installed on a separate physical HD from the host machine.  Things seem to run a bit nicer that way.

---

### Post by ubfu on 2009-10-01
That's why I need some people who are using quad core processor can give a few guidance 

Thank you

---

### Post by gnuvistawouldbecool on 2009-10-02
I have had reasonable success running virtualbox (in XP) with 1.35GB RAM, 1.8GHz AMD turion 64, using an Ubuntu guest.  With guest additions, I was able to get it running Compiz, if a little slowly.

With it in seamless mode it was usable for what I wanted, but I wouldn't really recommend that experience.

---

### Post by The Jinx on 2009-10-04
i have no problem running it on a lappy with a AMD 1.8ghz Dual Core with 2gbs of ram, and im running Vista as the Guest OS

---

### Post by ubfu on 2009-10-04
yes indeed I get my work done with printer driver on window xp. but once install with more than a few programs things starting to get lagging behind.

I am quite sure vista utilize memory far more better than window xp.

Every clicks of folder or file or a program , the single core which allocated will jump up to 100% until program finish loading or file successful loaded.It's normal to use cpu usage but 100% for a 2.0ghz , just wanted to confirm how does window xp sp2 cpu history opening an application closing , draging and browsing youtube.

---

### Post by Dedoimedo on 2009-10-05
> **ubfu said:**
> That's why I need some people who are using quad core processor can give a few guidance 

Thank you

You do not need quad-core to run virtualization with good results.

I have a 3 year old machine with 2gb ram only, dual core, 2 7200rpm disks with virtual machines on the second disk, it can easily and with good results run 3 512-mb instances of centos, for example, or 1 xp, 1 centos, 1 ubuntu, etc.

Your biggest bottleneck is the disk ... Even a single-core cpu won't matter much if you don't churn the cpu to max.

Dedoimedo

---

### Post by maxxjr on 2009-10-06
I played with VirtualBox briefly a couple of months ago.  

I recall reading somewhere that there is an option for something like IO APIC.  If on, it will degrade system performance.  The option is required if you want your guest OS to have more than one CPU, but optional if your guest OS will only have one CPU.  

I found that both the host and guest OS ran better with one "virtual CPU" on the guest and the IO APIC option off vs. dual virtual CPU's on the guest with IO APIC on.  In my case, it took almost 3x the time to boot a dual CPU XP guest vs. single.  I didn't take measurements, but the host OS was noticeably more "sluggish" while the dual-CPU guest was running.

I posted a question about this on the VirtualBox.org forums, and received a response that this is a known issue, and is being worked on.

I would recommend turning off the IO APIC option, even if it means you have to reinstall the guest OS for one CPU.  (I am writing this from memory, so "IO APIC" may not be correct, but it is an option that is required for multi-CPU guests).

---

