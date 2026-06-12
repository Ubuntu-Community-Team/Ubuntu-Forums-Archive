---
title: "VMWARE Player 5, Can't Cut and Paste from linux host to guest"
date: 2012-11-13
forum: Virtualisation
---

### Post by Daddyo-613 on 2012-11-13
**My Host System:**
O/S:                        Ubuntu 12.04 (precise)
Kernel:                   3.2.0-32-generic-pae
CPU:                       Intel(R) Core(TM)2 Quad CPU           @ 2.40GHz
VMWare Player: 5.0.1 build-894247

**My Guest System:**
O/S:                        Windows XP Professional Version 2002 SP 3 Updated to Nov-13, 2012
VMWare Tools:  9.2.2 build 893683 Installed[B]

My Problem:[/B]       I can't cut and paste or drag and drop files from my host to my guest. I could do this before installing VM Player 5 and I could even briefly do it when I first installed the new player.

                               When I copy a file folder on my host and move back to the guest window and click on it to engage the mouse in the guest system and then paste, a dialogue box from the host comes up showing the folder and its contents being copied but when that process is complete the folder does not appear in the guest system, the file folder I was pasting the files into displays the windows wait icon and the virtual cpu shoots up to 100% and remains there without completing until I force a shutdown.

                              The process displayed in the Windows Task Manager is "vmtoolsd.exe". On shutdown of the guest that file is forced to quit.[B]

Solutions I've Tried:
[/B]
I've un-installed and then reinstalled VMWare Player bundle as root in accordance with the MVWare PDF manual but to no avail.

Can someone please give me some guidance. It's supposed to work and did before.

---

### Post by dcstar on 2012-11-14
> **Daddyo-613 said:**
> 
.........
Can someone please give me some guidance. It's supposed to work and did before.

Works fine on my system with similar setup.

---

### Post by ThrashManiac on 2013-03-12
Have someone tried that drag-and-drop function with Vmware Player? I have tools installed. Guest: Win98, host: Ubuntu 12.04 64bit.

P.S. I have tried that yesterday and it worked great. Vmware tools are required.

---

