---
title: "[SOLVED] Windows Vista driver error related to registry."
date: 2008-10-07
forum: Windows
---

### Post by Raccoon1400 on 2008-10-07
A few days ago I thought I'd try to update my abandoned vista install. This laptop dual boots Vista/Archlinux.

I installed AVG and threatfire. AVG told me I had a trojan. I went after that for a while, even tried to kill it with regrun. At one point, it told me this registry key was infected, and I tried to get it to delete it, but I don't think it did. In the end, it turned out to be threafire antivirus fighting with each other.

Now, the real problem. My keyboard and touchpad don't work anymore. When I go to the properties box, it tells me this.
```

Windows cannot start this hardware device because its configuration information (in the registry) is incomplete or damaged. (Code 19)

Click 'Check for solutions' to send data about this device to Microsoft and to see if there is a solution available.
```

The windows help website was not useful because it only had solutions for XP, which didn't work for me.

Any suggestions, or will I have to reinstall.

---

### Post by smoker on 2008-10-07
have you tried 'system restore'?

---

### Post by Raccoon1400 on 2008-10-07
> **smoker said:**
> have you tried 'system restore'?

It wasn't enabled. Bloody microsoft, having it disabled by default.

---

### Post by smoker on 2008-10-08
> **Raccoon1400 said:**
> Any suggestions, or will I have to reinstall.

you shouldn't have to reinstall the operating system cause of this, try reinstalling the drivers from the laptop manufacturers support site. if that doesn't work you should be able to do a 'repair' from the windows install disk, which may fix the registry.

best of luck

---

### Post by Raccoon1400 on 2008-10-08
> **smoker said:**
> you shouldn't have to reinstall the operating system cause of this, try reinstalling the drivers from the laptop manufacturers support site. if that doesn't work you should be able to do a 'repair' from the windows install disk, which may fix the registry.

best of luck

I'll try the repair thing from the disk. I tried reistalling the drivers from my dell disk. That gave me an error messge. It did install, but it didn't work.

I'll try the repair. Will how to do the repair be obvious when I boot the disk, or do I need further instruction.

---

### Post by smoker on 2008-10-08
hi, i've never done a 'repair' install for vista, but there is some info here:
[http://www.vistax64.com/tutorials/88236-repair-install-vista.html](http://www.vistax64.com/tutorials/88236-repair-install-vista.html)

a repair install shouldn't interfere with your data, but it is always best to backup essential stuff first,

best of luck

PS: as you dual boot, you will probably have to reinstall Grub afterwards!

---

### Post by Raccoon1400 on 2008-10-08
I did the repair install and now everything seems to work. I used super grub disk to fix grub.

---

