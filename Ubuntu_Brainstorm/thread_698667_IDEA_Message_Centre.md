---
title: "IDEA: Message Centre"
date: 2008-02-16
forum: Ubuntu Brainstorm
---

### Post by Martje_001 on 2008-02-16
Hi,
Some updates screw something up. We may need a message centre for this. Maby a icon in the tray is needed for this.

---

### Post by Whiffle on 2008-02-16
That assumes that the computer knows there is something wrong.  My computer has yet to tell me its broken, it just lets me figure it out.  

I do think a list of potential errors from an update wouldn't be a bad idea, so you can update your computer when you know you have time to actually fix it, otherwise you could be really up a creek.  Thats why I almost never update mine, if its working i leave it alone.  I need it to be reliable and not subject to the latest fad in update errors.

---

### Post by Martje_001 on 2008-02-16
> **Whiffle said:**
> That assumes that the computer knows there is something wrong.  My computer has yet to tell me its broken, it just lets me figure it out.
The messages are downloaded from ubuntu.com.

There was a root exploit a week ago (or something), and there came an (quick and dirty) update for a new kernel. Since I dual-boot with Windows, my windows entry in /boot/grub/menu.lst was gone.
The Ubuntu devopers could have send me a message via Message Centre.

See my point? ;)

---

### Post by 23meg on 2008-02-16
[QUOTE=Martje_001]
There was a root exploit a week ago (or something), and there came an (quick and dirty) update for a new kernel. Since I dual-boot with Windows, my windows entry in /boot/grub/menu.lst was gone.[/QUOTE]

Assuming that you did nothing wrong and there's nothing unsupported on your system that interferes with the process, it shouldn't have been. If it's going to be broken anyway, there's no point in sending you a message saying "We're about to break your Windows installation, would you like to continue? Y/N". 

Also, you can already see details regarding changes that each update will apply in the update manager.

---

### Post by chrisccoulson on 2008-02-16
> **Martje_001 said:**
> The messages are downloaded from ubuntu.com.

There was a root exploit a week ago (or something), and there came an (quick and dirty) update for a new kernel. Since I dual-boot with Windows, my windows entry in /boot/grub/menu.lst was gone.
The Ubuntu devopers could have send me a message via Message Centre.

See my point? ;)

Any Windows entry in your menu.lst should be after the line that reads:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
If that is the case, your Windows entry should never be affected by update-grub, which is run during a kernel upgrade. I've dual-booted with Windows since Breezy, and I've never ever lost access to Windows after a kernel upgrade - including the one last week. If your menu.lst was created by the installer and you haven't messed around with it, then the update is broken, and you should report it as a bug.

I agree with 23meg. Supported updates should never break the system. I don't want to be notified of an update that might break the system. I want updates that *don't* break my system.

---

