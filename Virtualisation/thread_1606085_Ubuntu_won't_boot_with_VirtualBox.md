---
title: "Ubuntu won't boot with VirtualBox"
date: 2010-10-26
forum: Virtualisation
---

### Post by Resist on 2010-10-26
I recently installed Ubuntu with VirtualBox, it was working fine for a couple of weeks.  Yesterday I think I must have force shutdown the machine, it messed something up and now it won't boot.

I get this message:

```
mount: mounting /dev on /root/sys failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init.
No init fount.  Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for a list of build in commands

(initramfs)
```

I have similar problems to this before on my other computer and was unable to fix it.  I did some searching and people were saying to boot from LiveCD and run some commands that way.  However I don't know how to boot from CD in a VM, if I hit F12 nothing happens, if I hold down F12 I get the Grub Menu.

Can anyone help me out here please?

Thanks very much.

---

### Post by dcstar on 2010-10-26
> **Resist said:**
> I recently installed Ubuntu with VirtualBox, it was working fine for a couple of weeks.  Yesterday I think I must have force shutdown the machine, it messed something up and now it won't boot.
...........
Can anyone help me out here please?

Thanks very much.

Ask in the Virtualization forum.

---

### Post by Resist on 2010-10-26
OK can a mod please move it there.

---

### Post by dcstar on 2010-10-26
> **Resist said:**
> OK can a mod please move it there.

This is a forum read by users, "mods" only act on what **you** ask them to do.

Use the "Report Abuse" function yourself to request a move.

---

### Post by Resist on 2010-10-26
OK sorry, I'm not familiar with the formality here.

---

### Post by s.fox on 2010-10-26
Thread moved to [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308") at op request.

---

### Post by Resist on 2010-10-26
Thanks s.fox

If I check the box for the VM to only boot from CD then I get this message:

```
FATAL: No bootable medium found! System halted
```How am I meant to boot into the LiveCD and if I can am I able to re-install GRUB to fix the problem?

---

