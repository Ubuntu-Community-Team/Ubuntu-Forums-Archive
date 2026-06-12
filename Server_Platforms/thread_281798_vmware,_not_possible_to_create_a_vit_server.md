---
title: "vmware, not possible to create a vit server"
date: 2006-10-21
forum: Server Platforms
---

### Post by mwthrane on 2006-10-21
Hi

I just installed vmware server console and fired it up by typing vmware in terminal. It starts up just fine. But the only possibility i have is to connect to a server. All other buttons are grey, as in they dont do anything if i press them. What i want is to install windows xp,

I followed this guide:
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

How do i enable vmware to do other things than just connect?

---

### Post by elst on 2006-10-21
> **mwthrane said:**
> Hi

I just installed vmware server console and fired it up by typing vmware in terminal. It starts up just fine. But the only possibility i have is to connect to a server. All other buttons are grey, as in they dont do anything if i press them. What i want is to install windows xp,

I followed this guide:
[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

How do i enable vmware to do other things than just connect?

Did you enter your serial number (Help > Enter Serial Number)?

IIRC, you need to enter your serial number before Vmware lets you actually do anything.

---

### Post by mwthrane on 2006-10-21
I entered my serial number in the terminal when i installed it. But ill check it out.

---

### Post by mwthrane on 2006-10-21
enter serial number is also greyed out.

---

### Post by elst on 2006-10-21
D'oh: since this is the management console, it can't do anything before it successfully connects to the main Vmware service - the console for Server is just a client. I should have thought of that before.

---

### Post by elst on 2006-10-21
What you'll need to do is fire up the management console, connect to a server, put the XP disk in the server computer, and then go through the process of creating a virtual machine.

With the Workstation product the graphical interface automatically manages the VMware facilities on that computer, and can't control remote servers.

Hope that helps

---

### Post by mwthrane on 2006-10-21
Hahaha, i feel so stupid now. Thanks a bunch.

---

