---
title: "headless server problem booting"
date: 2012-10-05
forum: Server Platforms
---

### Post by groeneb on 2012-10-05
I have an Intel d2700dc mainboard with a crucial m4 128GB ssd running ubuntu 12.04 server. I'm busy getting the machine to run headless (without monitor). Unfortunately it won't boot without a monitor attached. It has to do something with the grub boot loader.

Tried the solution here but it doesn't work:

[https://bbs.archlinux.org/viewtopic.php?id=141274](https://bbs.archlinux.org/viewtopic.php?id=141274)

Some hints would be appreciated

---

### Post by anonymouschief on 2012-10-15
If your system boots OK when a monitor is connected, try your BIOS settings. There is usually a setting that can be set to ignore BIOS errors if the error is from the keyboard, mouse, or display. So when your system fails to find these devices, it still continues to boot. Your motherboard actually supports this feature.

For your reference, I have extracted the following text from page 67 your motherboard's user guide:

**3.7.3 Booting Without Attached Devices**
For use in embedded applications, the BIOS has been designed so that after passing
the POST, the operating system loader is invoked even if the following devices are not
present:
[LIST]
[*]Video adapter
[*]Keyboard
[*]Mouse
[/LIST]

Reference: [http://downloadmirror.intel.com/20715/eng/D2700DC_TechProdSpec02.pdf]("http://downloadmirror.intel.com/20715/eng/D2700DC_TechProdSpec02.pdf")

I hope this helps.

---

### Post by groeneb on 2012-10-17
The problem is not in the startup but in de grub boot loader. For now I've temporarily connected a monitor.

---

### Post by darkod on 2012-10-17
Can you elaborate more about the grub error message, etc?

I have a headless server running the previous LTS, 10.04, without any problems.

It could be related to your hardware combination though.

---

