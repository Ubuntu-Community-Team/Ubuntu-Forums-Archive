---
title: "After kernel update Ubuntu keeps asking &quot;Restart Required&quot; to finish update."
date: 2009-08-18
forum: System76 Support
---

### Post by samalex on 2009-08-18
Hi,

This morning when I booted-up, Ubuntu came up with the message saying there were updates available, one of which was a kernel update to 2.6.28-15 (I was on 2.6.28-14).  I let it install all the suggested updates (there were about a dozen of them), and it said Restart Required.  

I did the restart but running 'uname -a' still showed I was on 2.6.28-14.  About a minute after the restart it came up again saying a restart was required again, so I clicked Restart and it went down and came back up a second time though it was still running 2.6.28-14 afterwords.  Now a third time it's asking to restart yet again.  Am I stuck in a loop?

Has anyone updated to 2.6.28-15?  And if so did you run into this?  I'm running a PanP5 system with a stock version of Ubuntu, besides a few third-party apps through Synaptic.

Thanks --

Sam

---

### Post by kpkeerthi on 2009-08-18
Check in the GRUB menu which kernel you have selected.

---

### Post by samalex on 2009-08-18
[QUOTE="kpkeerthi"]Check in the GRUB menu which kernel you have selected. [/QUOTE]

Grub looked okay, but what looked like was happening was clicking "Restart Now" only restarted X and not the entire system.  I instead clicked "Restart Later" and manually shut down the system.  When it came back up it of course hit Grub and loaded the 2.6.28-15 kernel.  

For a second there I thought Ballmer had sneaked something in on that last update :)

Sam

---

### Post by jml on 2009-08-18
That worked for me as well, samalex.  Thanks.

Joe

---

### Post by Mastermind007`` on 2010-01-13
Had the same issue here. Fresh install as a VM on ESXi 3.5 server. Installed all recommended update (no third party). Restart was not actually restarting the system just X. Selected restart later and did a proper restart and all is working now.

uname -a state running kernel 2.6.31-17

---

### Post by thomasaaron on 2010-01-14
That definitely sounds like a bug. I've not seen that happen before. Good job figuring it out though. At least it was easy. :D

---

### Post by luca.marinosci@gmail.com on 2010-01-14
Happens to me too x.x

But fixed as said up there :)

Manually rebooted and everything was fine.

---

### Post by samalex on 2010-01-14
Every time a kernel update or any update that requires a reboot happens, I just cancel the message box asking if I want to reboot and manually do so... that's the only way I've found to get past it since the "Reboot Now" message does only restart X.

Yeah, a bug but nothing too crazy since rebooting only takes 30-40 seconds if that on my PanP5.

Sam

---

### Post by thomasaaron on 2010-01-14
I've got a bunch of updates waiting. I'll run them and post back when I reboot my machine. Ping me if you don't hear from me by Monday on it. I'll be out of the office tomorrow.

---

### Post by thomasaaron on 2010-01-14
OK, scratch that. I ran update, which included the -17 kernel and selected "Restart Now." X hung on the restart so I went into a terminal and restarted gdm.

But when I check the kernel I'm running, it's the -17.

So, it's not a reproduction of your problem, but it was wonky.

Let's pick it up next week and I'll image a Pangolin and get more scientific with it.

---

