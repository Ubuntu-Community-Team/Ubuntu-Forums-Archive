---
title: "Saying (writing) Ubuntu / Linux"
date: 2023-08-28
forum: Ubuntu, Linux and OS Chat
---

### Post by jsdata on 2023-08-28
Hi,
I'm new here.
So when I want to discuss something CLI related, then I address to Linux, when GUI stuff, then I address Ubuntu (my install), right ?
... or are there some Ubuntu specific commands ?

---

### Post by Rubi1200 on 2023-08-28
Welcome :-)

Not sure what you mean. Can you give a couple of examples?

---

### Post by ian-weisser on 2023-08-28
> **jsdata said:**
> [W]hen I want to discuss something CLI related, then I address to Linux, when GUI stuff, then I address Ubuntu (my install), right ?
... or are there some Ubuntu specific commands ?

"Ubuntu" usually refers to the entire software system, including the Linux kernel, the CLI system (which is completely separate from the kernel), and the "GUI stuff".

Each of those is produced by some upstream project(s). The Ubuntu Project integrates that upstream software and distributes the integrated result. Canonical Ltd, on behalf of the Ubuntu Project, maintains infrastructure (build farms, software repositories, support forums, etc.) for integration, distribution, and support.

When you want to discuss something, just try to be clear about what you want to discuss. Avoid shorthand.

---

### Post by jsdata on 2023-08-29
Thanks guys :)

---

### Post by grahammechanical on 2023-08-29
> or are there some Ubuntu specific commands ?

I know of two Ubuntu commands. It is not necessary to know them but if we are running more than one Ubuntu installation there might be an occasion where we need to run them. Ubuntu uses a bootloader called GRUB (Grand Unified Bootloader). The two commands are update-grub and grub-install. Each of them invokes certain Grub commands. It  is not easy to update or re-install Grub using the Grub commands themselves, So, those two Ubuntu commands make things easier for us.

There is something else you might want to get familiar with. It is called Friendly Recovery. If we have more than one operating system installed the Grub boot menu will always appear and allow us to select which OS to load.

If we only have Ubuntu installed then we will not see the Grub boot menu. To call up the menu we press the shift key several times as the machine first starts to boot up

The boot menu has an Advanced Options for Ubuntu choice. Select Advanced Options and we get a recovery menu. The options in this menu will run certain commands that could help us fix problems. I think it is sensible to be familiar with the recovery menu.

The Grub boot menu also offers an option to open the UEFI settings utility.

Regards

---

