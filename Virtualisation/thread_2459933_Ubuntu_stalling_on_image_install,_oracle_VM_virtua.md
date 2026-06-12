---
title: "Ubuntu stalling on image install, oracle VM virtualbox"
date: 2021-03-29
forum: Virtualisation
---

### Post by lewsutt on 2021-03-29
I would like to ask for help getting my Ubuntu vm set up. The problem may lay with my windows 10 configuration, but thought I would start here. I did a clean install of windows 10 last month, and ever since then I have not been able to get virtualization to work. The machine starts to load, then gets stuck on the black screen with the spinning circle. The circle stops spinning, the screen freezes, and my CPU raises 10 degrees C.

My system: Auros Gigabyte x570 elite (renound for virtualization issues I know), Ryzen 3700, Windows 10. I also started mining ethereum using betterhash, which might have caused the issue as well. My bios is the latest version, and I have SMT enabled. I would be happy to provide logs or any other information if you can tell me what you need. Thanks team!

---

### Post by CelticWarrior on 2021-03-29
Welcome.

A couple of things to check first: Enable AMD virtualization in UEFI and disable Hyper-v (or whatever) in Windows if you're using Virtualbox.
Other thing: Are you sure you have installed all the required drivers in Windows?

---

### Post by lewsutt on 2021-03-29
I have SMT enabled in bios, and hyper-v disabled in windows. Not sure about the drivers, but my system and bios are up to date. Which drivers should I check?

---

### Post by lewsutt on 2021-03-29
My bad, I meant SVM mode is enabled in bios. I guess that is Gigabytes version of AMD-v.

---

### Post by CelticWarrior on 2021-03-29
Re: drivers you should install the latest AMD software.

What resources are you assigning to the VM?

---

### Post by lewsutt on 2021-03-29
I got an answer from virtualbox forums, which might help me when I get a sec. Turns out that even though I do not have hyper-v enabled, something is using it and blocking AMD-v from using virtualization. It looks like there is an administrator command prompt followed by a cold boot that might fix my issue. 

The VM is getting MB video ram, monitor, VMSVGA, no 3D acceleration, PIIX4 IDE controller with my install image, a SATA controller with 40G storage I think. 8G RAM, 8 CPUs. I'm not sure what else to say as far as resources, but happy share.

---

### Post by CelticWarrior on 2021-03-30
8 CPUs is probably too much. You only have 8 cores actually and thanks to hypertreading you get 16 usable cores but only half are "real". Ubuntu in a VM works fine with one or two, up to 4 should be fine but 50% of the processing power can seriously hurt the host, especially when the host is Windows. Ditto for the memory, 8GB is good for Ubuntu (4GB would be tight) but only assign less than 50% of total memory.

---

### Post by lewsutt on 2021-03-30
Duly noted, thank you.

---

### Post by lewsutt on 2021-03-30
Thanks for the guidance on setting up my machine. It turns out that a search into the first log for **[COLOR=#800080][FONT=&amp]Attempting fall back to NEM[/FONT][/COLOR]** shows that hyper-v was in use, and I was advised to reboot, enter command prompt as admin, then enter **[COLOR=#800080][FONT=&amp]bcdedit /set hypervisorlaunchtype off[/FONT][/COLOR]** and **[COLOR=#333333][FONT=&amp][COLOR=#800080]DISM /Online /Disable-Feature:Microsoft-Hyper-V[/COLOR][/FONT][/COLOR]** followed by a 20 second cold boot. This solution came from scotgus1 in the virtualbox forums. Here is the link if that is allowed, if not please remove. Thanks again everyone.  [https://forums.virtualbox.org/viewtopic.php?f=25&t=99390](https://forums.virtualbox.org/viewtopic.php?f=25&t=99390)

---

