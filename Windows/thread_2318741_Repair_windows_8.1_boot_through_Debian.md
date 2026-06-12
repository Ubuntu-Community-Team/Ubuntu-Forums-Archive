---
title: "Repair windows 8.1 boot through Debian"
date: 2016-03-28
forum: Windows
---

### Post by joop3 on 2016-03-28
I screwed up my Windows 8.1 boot with Easybcd. I checked some box that said count down from 5 seconds in the edit boot section now if I boot in UEFI boot it says windows cannot boot insert repair disk and if you don't have the repair disk contact manufacturer. If I boot in CSM boot mode I can get to Debian 8 grub menu but windows is not on it. I want to use Grub customizer to be able to boot windows and maybe have windows show up on the Debian grub menu if it is not to risky.

---

### Post by X-RED_Tech on 2016-03-28
Not possible.
You need Windows recovery media.

---

### Post by Bucky Ball on 2016-03-29
*Thread moved to **Windows**.*

Forget grub customizer for the moment. Can you boot into Debian? If so, open a terminal and:

> sudo update-grub

Reboot. Any sign of Windows? If no luck, try [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). You'll find it with a quick search.

You have two separate questions here. The first one is that you can't boot Windows. The second is getting Windows on the Debian grub, neither of which has anything to do with Windows. 

Suggest you concentrate on fixing Windows, and you may have more luck on a Windows forum, and then get Windows on the Debian grub, where you will probably find most help on a Debian forum. We have a sub-forum for Debian here which is in the same section as this Win sub-forum, but not the most effective place to be posting. Wherever you post, without more info than what you've given it will be hard to give much support.

Good luck.

PS: > windows cannot boot insert repair disk and if you don't have the repair disk contact manufacturer.

Any reason you haven't done this? Am I correct in presuming you have no recovery disk for Win? Can I assume this is a bootleg copy of Win? Be aware of this from the forum Code of Conduct.

> We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings.

---

### Post by X-RED_Tech on 2016-03-29
Boot repair will probably tell him there's one OS in BIOS and other in UEFI...

---

### Post by Bucky Ball on 2016-03-29
> **X-RED_Tech said:**
> Boot repair will probably tell him there's one OS in BIOS and other in UEFI...

And the bootinfo script output it produces will give a heck of a lot more detail besides ...

---

