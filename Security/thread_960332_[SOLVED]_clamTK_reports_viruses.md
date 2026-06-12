---
title: "[SOLVED] clamTK reports viruses"
date: 2008-10-27
forum: Security
---

### Post by bwallum on 2008-10-27
Hi

My machine has never run better, I'm fired up with Intrepid. However I thought I would run clamTK for the hell of it and it found 5 viruses apparently.

When I checked the quarantine window 3 entries were listed (screenshot attached). 

Should I be worried?

---

### Post by bwallum on 2008-10-27
Now I'm worried. I shut down my machine and rebooted some time later. I was offered the CLI only. I presume this is because gdm has been quarantined by clamTK. (A message says that it can't find gdm.)

I tried 'sudo apt-get update', then 'sudo apt-get install ubuntu-desktop' but no luck.

I am now using my Hardy installation to communicate.

Any ideas on how to recover my Intrepid desktop please, using the command line only?

---

### Post by bwallum on 2008-10-27
Solution:

At the command line type startx
When the desktop comes up go to System>Administration>Synaptic Package Manager
Search for gdm
Select reinstall package and apply
Reboot the pc (you might have to simply switch it off)

---

