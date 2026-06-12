---
title: "Server stops for 1-5 hours upon boot unless an unknown task is manually terminated."
date: 2009-02-11
forum: Server Platforms
---

### Post by GeneralNMX on 2009-02-11
My headless-turned-non-headless Ubuntu Hardy server stops for 1-5 hours upon boot unless an unknown task is manually terminated. It's right after the mdadm raids are defined. If I do a Sysrq+Alt+e, I'll see "Terminated. Done." in the boot log. What is it doing? Some mdadm task? It can't be doing fsck because I disabled fsck passes under /etc/fstab AND did tune2fs -c 0 -i 0 to all my partitions.

The dmesg and kernel logs just say "Terminated. Done.", so how can I figure out what it's doing? Sysrq+Alt+t gives me way too much info on the screen that I can't scroll, and I can't bg the process to drop down to a terminal to figure out what the heck it is.

I'm looking for a route to diagnose this mess and get it back to being headless.

---

### Post by cariboo on 2009-02-11
Seeing as you have a monitor hooked up to your server, run top at the prompt and see if there is anything unusual running.

Jim

---

### Post by GeneralNMX on 2009-02-11
Nope -- nothing unusual. I've already terminated the process by sending Sysrq+Alt+e. I guess I'll have to make some marks in the runlevel scripts around and in mdadm. Just figured out I could do that.

---

