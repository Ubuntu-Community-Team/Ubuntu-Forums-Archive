---
title: "&quot;sudo reboot&quot; causes system shutdown"
date: 2012-03-09
forum: Server Platforms
---

### Post by klausmedk on 2012-03-09
Hello

When I issue "sudo reboot" on my ubuntu server 10.04 it sometimes (not every time) shuts down instead of rebooting.

Is this a known problem?
Where should I look for clues related to this problem? 
Should I look in the syslog or other logfiles?

//Klaus Jacobsen

---

### Post by wyliecoyoteuk on 2012-03-09
I would use:
```


sudo shutdown -r now


```

---

### Post by pinjan on 2012-03-10
I am using
 ```
 sudo reboot -h now
```

Has worked always with my server for rebooting.

---

### Post by codemaniac on 2012-03-10
> **pinjan said:**
> I am using
 ```
 sudo reboot -h now
```

Has worked always with my server for rebooting.

the -h switch will halt the system istead of rebooting , you need to use the -r switch with shutdown to reboot .

---

### Post by spynappels on 2012-03-10
Or use 
```
sudo shutdown -P now
```

---

### Post by matt_symes on 2012-03-10
Hi

What happens when you change the run level ?

```
sudo telinit 6
```

Kind regards

---

### Post by spec_v on 2012-04-16
I'm having the same problem on an older Toshiba laptop.   Reboot or shutdown -r worked with FreeBSD on the same machine but now with Ubuntu 11.10 server, it will just shutdown.  Kind of a pain.  Especially when trying to reboot the server remotely.

Anyone have any ideas?

---

### Post by matt_symes on 2012-04-18
Hi

Have you tried a new reboot method ?

from reboot.c in the kernel sources.

```
/* reboot=b[ios] | s[mp] | t[riple] | k[bd] | e[fi] [, [w]arm | [c]old] | p[ci]
   warm   Don't set the cold reboot flag
   cold   Set the cold reboot flag
   bios   Reboot by jumping through the BIOS (only for X86_32)
   smp    Reboot by executing reset on BSP or other CPU (only for X86_32)
   triple Force a triple fault (init)
   kbd    Use the keyboard controller. cold reset (default)
   acpi   Use the RESET_REG in the FADT
   efi    Use efi reset_system runtime service
   pci    Use the so-called "PCI reset register", CF9
   force  Avoid anything that could hang.
 */
```

These are kernel command line switches just like any other.

Kind regards.

---

