---
title: "VMWare Playeer works good with Kernel 5.04 but very bad with 5.15"
date: 2022-11-30
forum: Virtualisation
---

### Post by tommaso81 on 2022-11-30
I installed VMplayer ( tested 17.0, 16.2.4, 16.1.2) on Ubuntu 22.04. Running both, Linux (xubuntu 20.04) or windows, under this machine is very slow and Interrupts service (under windows7) goes to very high CPU consumption. The musical tone at boot comes very ugly.  So I tried to install under a new hard disk Ubuntu 20.04.5 that it is still with kernel 5.15. Things are slight better but Interrupts service still bad, the music tone at boot of windows7 now is perfect but if I see cpu % I continue to have big peaks.

So I installed:
sudo apt install linux-generic

and rebooted Ubuntu 20.04 with Kernel 5.4.

Now VMWare works perfectly and performances of emulated machine seem the same of a native machine.

So the question is:
why ?
I tried to start Ubuntu 22.04 with kernel 5.4 but it doesn't work. Is there a way ?

Thank you very much

---

### Post by slickymaster on 2022-11-30
*Thread moved to **Virtualisation**.*

---

