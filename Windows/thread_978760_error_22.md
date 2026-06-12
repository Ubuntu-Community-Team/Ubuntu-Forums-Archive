---
title: "error 22"
date: 2008-11-11
forum: Windows
---

### Post by rstimpymike on 2008-11-11
i totally just screwed up my computer. i am running vista and ubuntu on my comp. i need to get rid of the the ubuntu partition so that it is strickly vista. so i deleted the ubuntu partition and now my computer wont turn on can anyone fix this?

---

### Post by insane_alien on 2008-11-11
pop your vista disk in go to the recovery console and run 'fixmbr'

you deleted grub without replacing the windows bootloader master boot record so your BIOS didn't know where to look to find what it needed to boot the OS.

---

### Post by rstimpymike on 2008-11-11
i bought my computer refurbed...it didnt come with a disk

---

### Post by prshah on 2008-11-11
> **rstimpymike said:**
> i bought my computer refurbed...it didnt come with a disk

Use the super grub disk: Here's a handy [link]("http://www.cyberciti.biz/tips/super-grub-disk-fix-windows-linux-boot.html")

---

### Post by rstimpymike on 2008-11-11
the "new" aka crappy old computer that im using has no cd burner does anyone know how to boot ubuntu via usb drive

---

