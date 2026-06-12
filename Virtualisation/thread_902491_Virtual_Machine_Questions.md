---
title: "Virtual Machine Questions"
date: 2008-08-27
forum: Virtualisation
---

### Post by Piro24 on 2008-08-27
Hello :) I'm currently in the process of backing up all of my important personal files (music/videos/game saves) to DVD's, since Windows has crashed, yet again, and this time not even system restore will get it back. So I've decided to give up on windows, change my partitions to all Linux (ubuntu).

However, I have not given up on gaming, so I am planning to use a virtual machine for that, now for the questions.

1: Will I be able to play games at a reasonable speed using a Virtual Machine? I suppose it depends on how much resources I allow the VM to use, correct?
2: Is it possible to access my filesystems (ext3) from within a virtual machine, or would I have to put all my games into the virtual harddrive that windows will use?
3: Would it be a problem if I gave most of my system's resources to the VM, how much would be too much on a laptop w/ 2 1.8GHZ processors, 2 GB RAM?
4: Which Virtual Machine works best for Ubuntu Hardy Heron (8.04)? The only VM I have ever used was a Mircosoft one, under windows, the first time I ever tried to install linux to try it out.

5: How safe as Virtual Machine's as far as stability goes? 

Thanks in advance to anybody who answers these questions, if you feel you can only answer one or two, please do, because I really want as much information as I can get about this, since this will be the first time I am completely abandoning Windows.

---

### Post by mellowd on 2008-08-27
vmware is rock solid, but forget about playing games through it. There is very limited 3d support.

I'd use wine for gaming.

---

### Post by Fire_Chief on 2008-08-27
I use Virtualbox (now called Sun xVM) to run Windows XP. It does not support 3d acceleration at all but works very well for everything else. 
It is possible to access the linux filespace from within the VM but to Windows it appears as a mapped network drive instead of a local disk.
I would suggest starting with giving the VM 512MB of RAM and work up from there if you feel you need to. Don't allocate too much or your host performance will suffer.

I second the recommendation for gaming under Wine. You should also see if the games can run natively.

---

### Post by tuxxy on 2008-08-27
1: Will I be able to play games at a reasonable speed using a Virtual Machine? I suppose it depends on how much resources I allow the VM to use, correct?

**Not any high end games, simple games if any.**

2: Is it possible to access my filesystems (ext3) from within a virtual machine, or would I have to put all my games into the virtual harddrive that windows will use?

[B]You can access other drives using virtualbox yes, no need to create a virtual drive if you dont want.
[/B]
3: Would it be a problem if I gave most of my system's resources to the VM, how much would be too much on a laptop w/ 2 1.8GHZ processors, 2 GB RAM?
[B]
Shouldnt be a problem, just make sure you saved some for linux to operate still[/B]

4: Which Virtual Machine works best for Ubuntu Hardy Heron (8.04)? The only VM I have ever used was a Mircosoft one, under windows, the first time I ever tried to install linux to try it out.

**I use virtualbox and it meets all my needs,**

5: How safe as Virtual Machine's as far as stability goes?

**Excellent**

---

### Post by mikewhatever on 2008-08-27
> 3: Would it be a problem if I gave most of my system's resources to the VM, how much would be too much on a laptop w/ 2 1.8GHZ processors, 2 GB RAM?

Yes. Consider that whatever resources you give to VM, are taken away from the host OS.

---

### Post by Piro24 on 2008-08-27
So basically, games will not run in the Virtual Machines, correct? Wine doesn't really do a good job of emulating my games, most are extremely laggy, or the graphics do not display correctly.

---

