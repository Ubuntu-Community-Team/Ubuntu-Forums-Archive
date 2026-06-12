---
title: "Where to locate WinXP and Win7 image files?"
date: 2010-08-23
forum: Virtualisation
---

### Post by evenrelation on 2010-08-23
Hello

Although this may seem like a trivial question to some, I haven't been able to google the answer yet.

I'm running Lucid on a Lenovo TP without an optical drive, and I want to usb-install either WinXP or Win7 on VirtualBox. 

Where exactly are the image files on the installation cd's, and what is the best (most secure) way to write them onto my 16GB USB drive?

Furthermore, on the XP cd it says "Only use this CD to reinstall the operating system on a Dell computer." Does it matter?

---

### Post by pricetech on 2010-08-23
> **evenrelation said:**
> Where exactly are the image files on the installation cd's, and what is the best (most secure) way to write them onto my 16GB USB drive?

Best answered on a windows forum or at microsoft technet.  They have tutorials there for what you want to do.

> **evenrelation said:**
> Furthermore, on the XP cd it says "Only use this CD to reinstall the operating system on a Dell computer." Does it matter?

Yes, it does.

---

### Post by TheFu on 2010-08-24
> **evenrelation said:**
> Furthermore, on the XP cd it says "Only use this CD to reinstall the operating system on a Dell computer." Does it matter?

Chances are that you have an OEM WinXP license that will not work on any computer other than a Dell, perhaps even the specific Dell model that it came with. It is not a normal install - it is tailored for Dell systems with specific drivers only. When it is all done installing, you may not have a system that boots, even under virtualization.

As to image files - you need to create one from the install CD using an ISO creation tool. Then tell virtualbox to use that at first boot when you setup the VM.

Good luck, but don't hold your breath.

---

