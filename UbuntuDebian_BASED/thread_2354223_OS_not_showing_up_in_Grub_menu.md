---
title: "OS not showing up in Grub menu"
date: 2017-02-28
forum: Ubuntu/Debian BASED
---

### Post by alf67 on 2017-02-28
I have just installed Subgraph (Debian-based) Linux and Qubes (Fedora-based) Linux on my SSD.  They are the only operating systems currently on my computer.  The grub menu was lost when I installed Subgraph & Qubes.  By booting from a Ubuntu 16.04 Live DVD and running Boot-repair (following instructions at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)), the grub menu is restored when booting.

However, the retored menu only shows one of the two operating systems choices.  I find I can only get either Subgraph or Qubes to show up but not both simultaneously on the grub menu.  I can get either Subgraph or Qubes to show up in the grub menu by running Boot-Repair from the Ubuntu Live DVD, going into Advance options, then choosing one of the operating systems as the default (they both show up as choices when choosing the default).  When the operating systems show up in the grub menu, they work when selected--the operating system starts up correctly and I can do a logon.

Not sure if this is relevant, but when Qubes starts up, it presents its own menu with 3 different Qubes "versions" to select from.  

The Boot-Repair program probably has an option to fix the problem, but I am not seeing where/how to do it.  

Here is a summary of the problem as well as output from the Boot-Repair program on the configuration of my computer.

_**Summary:**_

Want Subgraph Linux and Qubes Linux to both show up in grub menu.  These are the only operating systems on my computer.
My SSD is /dev/sdb
sdb1 = Subgraph Linux OS
sdb2 = Qubes Linux OS

_**Diagnostic Info from Boot-Repair:**_

[http://paste.ubuntu.com/24083253/](http://paste.ubuntu.com/24083253/)

---

