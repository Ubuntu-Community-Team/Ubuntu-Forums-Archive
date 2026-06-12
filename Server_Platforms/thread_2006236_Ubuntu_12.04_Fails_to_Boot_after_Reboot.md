---
title: "Ubuntu 12.04 Fails to Boot after Reboot"
date: 2012-06-18
forum: Server Platforms
---

### Post by auximini on 2012-06-18
I have installed Ubuntu 12.04 on several Dell c6220 servers (poweredge 12g). The install was successful and all hardware is recognized.

The problem that I am running into is that when issuing the reboot command or when pressing ctrl-alt-del, the server shuts down, but never comes back up. Instead, the fan revs up to full speed and stays that way until I power the server down.

Once the server has been powered down via the power button, Ubuntu will boot just fine -- until the next reboot.

I have found that by rebooting the server via the DRAC web interface will reboot the server correctly.

I have also found that this problem does not exist with CentOS -- I can press ctrl-alt-del all day long and it always comes back up.

I've tried several kernel parameters such as:

reboot=bios
reboot=pci
reboot=acpi
reboot=cold
reboot=efi
acpi=off
noapic

Nothing seems to work.

I have also tried upgrading to kernel 3.4, but no change there, either.

Has anyone run into a similar problem or any pointers on troubleshooting?

Thanks,

Joe

---

### Post by wilee-nilee on 2012-06-18
In the desktop, not sure of the server ctrl-alt-del is off, in the development where I'm at it logs out of X.

---

### Post by auximini on 2012-06-18
ctrl-alt-del issues a reboot as it should -- the same with the "reboot" command. The problem is that upon booting, the fan just revs, nothing comes up on the screen, and the server just sits.

---

### Post by bubylou on 2012-06-19
Do you have a screen attached to the server? If not could you hook one up to see exactly what step its hanging on. Could be just hanging at Grub waiting for you to pres enter.

---

### Post by auximini on 2012-06-20
It's hanging immediately when the server begins POST - before the Dell logo.

I've found that the kernel option "nolapic" allows the server to reboot normally. I'm currently looking into whether it is safe to have lapic disabled or not long-term.

---

### Post by andyt22 on 2012-07-04
I find that using the nolapic option disables all but one of the CPU cores on each processor at boot time - using dmesg to read the kermel messages while booting, the kernel correctly detects all the cores on all CPUs and then says the nolapic kernel parameter is set so it disables all but one of them.

We have dual 8 core CPUs in our server modules so including threaded cores, a total of 32 are detected on each server but with nolapic set, only one is actually enabled even with a SMP-capable kernel. So this option does not work for us. 

Andy

---

