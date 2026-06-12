---
title: "[SOLVED] add irqpoll boot option - headless"
date: 2008-12-28
forum: Server Platforms
---

### Post by jimmy the saint on 2008-12-28
I have a dell vostro box running hardy heron server.  It has a problem starting up without the irqpoll boot option being loaded to the grub kernel entry.  

Here is the dilemma.  The server is headless and maintained via ssh.  When the kernel gets updated, I have to add the boot option, or it spends hours trying to boot, sometimes successfully sometimes not.  Is there a way to edit the grub entries remotely?  this would have to be done while the grub menu is still active I think.

Is there another solution that I have overlooked?  I just don't want to have to pull out the server and set up a monitor/keyboard.  

Thanks

---

### Post by spiderbatdad on 2008-12-28
you can edit system files while logged in via ssh. Just run sudo vi or nano and edit /boot/grub/menu.lst 
No need to restart unless you want to test your changes.

---

### Post by jimmy the saint on 2008-12-29
Yes, but the problem is that after a kernel update the system will not boot.  I guess I just need to pay very close attention and remember to edit the grub menu and append the irqpoll option before I reboot into the new kernel.

---

### Post by gtdaqua on 2008-12-29
> **jimmy the saint said:**
> I have a dell vostro box running hardy heron server.  It has a problem starting up without the irqpoll boot option being loaded to the grub kernel entry.  

Here is the dilemma.  The server is headless and maintained via ssh.  When the kernel gets updated, I have to add the boot option, or it spends hours trying to boot, sometimes successfully sometimes not.  Is there a way to edit the grub entries remotely?  this would have to be done while the grub menu is still active I think.

Is there another solution that I have overlooked?  I just don't want to have to pull out the server and set up a monitor/keyboard.  

Thanks

To have the custom kernel switches automatically added to new kernels, add the switch to the line that begins with "#kopt" in the menu.lst file.

For e.g. if you want to add the switch "elevator=deadline" to your kernel, you normally would add:

```

kernel	/boot/vmlinuz-2.6.27-11-generic root=UUID=X ro quiet splash **elevator=deadline**

```

When the kernel gets updated, the new menu.lst will not include the new switch you added. In order to have the new switch added everytime during an upgrade, find the line that begins with "#kopt=" and add your custom switch to the end of the line.

E.g.:

```

# kopt=root=UUID=X ro **elevator=deadline**

```

Now the switch "elevator=deadline" will be automatically added to ALL kernel variables every time the kernel is upgraded.

---

### Post by jimmy the saint on 2008-12-29
Thank You!!  That is what I was looking for!

---

