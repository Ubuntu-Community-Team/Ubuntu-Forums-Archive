---
title: "833MHz vs 1066MHz DDR3: Will I feel a difference VMing?"
date: 2011-05-14
forum: Virtualisation
---

### Post by 3602 on 2011-05-14
So I'm VMing. Because I'd like to play with many different flavours of Linux (or maybe Windows) before multi-booting them.
I currently have 2*2GB 833MHz DDR3 (3.6GB usable reported) on my computer. The Turion II P540 can support a maximum of 1066MHz RAM speed.
I can mount 2*4GB 1066MHz DDR3 (Kingston) on this computer. 
When running Fedora 14 in VirtualBox (just keeping it open and idle), I get more than half RAM consumption; More when I'm doing something inside. Then my host Maverick can get a bit choppy.
So. If I upgrade that way, not too expensive, will I feed a speed increase?
Or: Grab another piece of SATA, chuck it in there (three drive bays, one used) and dedicate that one to VMing? 

Thank you very much.

---

### Post by fjgaude on 2011-05-15
I don't think you would notice any difference from the speed change from 833 to 1066, but doubling the about of RAM would help, as more of the things you do in the VM would end up in the cache. Even though you allocate just say, one gig to the VM, VMware will still put some of the programs into cache as needed. 

For WinXP I only use 512MB for it and VMPlayer uses up to a gig for all the apps I have in the VM.

---

### Post by 3602 on 2011-05-15
Well sooner or later I'll have to increase RAM. I am actually expecting to game inside a virtualized XP...

---

### Post by fjgaude on 2011-05-15
I don't think you will get very good gaming in any of the free vm makers, VMware Player, Virtual Box, etc. You have to pay VMware money to get a vm that has good 3D graphics. Low level games work in Virtual Box if you have the right video board. I'm not into gaming. I'm a retired graphic designer.

---

### Post by 3602 on 2011-05-15
Do you have any experience with the ATI FireGL "card"? Would that be a good choice or actual 3D graphics designing? Thank you.

---

### Post by fjgaude on 2011-05-16
No experience with ATI cards at all. I used Nvidia for years, but now I'm using the integral Intel GPU in the main processor chip. I really don't do 3D design. Everything is flat. Notice my signature and its link.

---

### Post by CharlesA on 2011-05-16
IMHO, VMs aren't really made for gaming. It might work, depending on your hardware, and what games you want to try, but don't expect miracles.

If you are really big into gaming, go for a dual boot solution.

Also, IIRC, that ATI FireGL card is an integrated card more suited for workstations then heavy gaming.

---

### Post by 3602 on 2011-05-16
Oh this thing got renamed into "FirePro" these days... 
I game when I have limited hardware, such as on a portable computer (OK, then there's Asus ROG...). The day I get meself a Leopard Xtreme (Syst76) or build a tower I'll go design 3D models. Animated and with actual physics and all.
Thanks.

---

