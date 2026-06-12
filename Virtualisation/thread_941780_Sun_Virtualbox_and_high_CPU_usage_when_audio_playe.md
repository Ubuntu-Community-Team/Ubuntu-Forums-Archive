---
title: "Sun Virtualbox and high CPU usage when audio played in guest"
date: 2008-10-08
forum: Virtualisation
---

### Post by Dillio187 on 2008-10-08
I have Virtualbox 1.6.4 installed under Hardy on a Latitude D630, T7250 cpu, 4gb memory (3.3 actual using 32 bit Hardy) and a 160gb 7200 rpm drive.

I'm running an XP guest under it, and when the machine is idle or doing other tasks, cpu usage is fine.  However, when I start playing audio using winamp, media player, or my sirius radio streamer, cpu usage shoots up to 50-60%.  Top shows it is the actual virtualbox app using the cpu, not anything else.

I have all the USB ports etc disabled for this guest, but that did not help.  Has anyone else had this issue or know of a fix for it?

---

### Post by Nasaki on 2008-10-08
Hmm... I dont think that is VirtualBox specific problem. I pretty sure that's just how VM's work. IT will obviously have very low CPU usage when the system is idling because the Guest OS is doing nearly no calculations. But, when any load is put on the Vm app your CPU usage is going to shootup like that. On another note, if you want to run winamp, have you tried Wine?

---

### Post by Dillio187 on 2008-10-08
> **Nasaki said:**
> Hmm... I dont think that is VirtualBox specific problem. I pretty sure that's just how VM's work. IT will obviously have very low CPU usage when the system is idling because the Guest OS is doing nearly no calculations. But, when any load is put on the Vm app your CPU usage is going to shootup like that. On another note, if you want to run winamp, have you tried Wine?

I had really bad luck with Wine, but I was trying to run outlook (2003 and 2007) in it, well I was actually running Crossfire but I digress.  My main use for the VM is Outlook and my Sirius streamer app, called Stream_On

The CPU usage in the guest itself is 1% with the audio app running, it would seem to me there is something wrong with how Virtualbox is passing the audio signal along to the audio within Hardy.

---

### Post by lamborghiniwang on 2008-11-25
I am having the same problem on a 64-bit Hardy host and a 32-bit Windows XP guest. taskmgr in the guest shows only 1% CPU usage, while the Virtualbox process in the host is using 50-60% CPU%.
The virtualbox has been updated to the latest v2.0.6

---

### Post by Dillio187 on 2008-12-04
I never found a solution to it, I did try Fedora 9 and that brought the CPU usage down to the 30% range, but that's still not real ideal.

---

