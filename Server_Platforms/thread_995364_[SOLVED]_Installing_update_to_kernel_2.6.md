---
title: "[SOLVED] Installing update to kernel 2.6"
date: 2008-11-27
forum: Server Platforms
---

### Post by maustin2 on 2008-11-27
I have successfully upgraded my kernel 2.6 utilizing ketchup- Applying 2.6.28-rc2-mm1.bz2. But all indications are that 2.6.15-52-686 is being loaded during boot. My current server is stable and I have backed up all essential files to a USB drive. What must I do to get 2.6.28 to load? I assumed ketchup would patch 2.6.15 to 2.6.28. This has proven to be a wrong assumption.

Any assist would be appreciated.](*,)

---

### Post by cariboo on 2008-11-27
You more then likely have to edit /boot/grub/menu.lst to use the new kerenel, as a custom compiled kernel doesn't have the init scripts needed to modify grub. you will have to edit this section to relect the new kernel from this:

```
title		Ubuntu 8.10, kernel 2.6.27-7 (Server)
uuid		9f702ef1-20bd-4aef-8f22-cd6830d83a50
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9f702ef1-20bd-4aef-8f22-cd6830d83a50 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
```

to something like this:

```
title		Ubuntu 8.10, kernel 2.6.28 (Server)
uuid		9f702ef1-20bd-4aef-8f22-cd6830d83a50
kernel		/boot/vmlinuz-2.6.28 root=UUID=9f702ef1-20bd-4aef-8f22-cd6830d83a50 ro  quiet splash
initrd		/boot/initrd.img-2.6.2.28
```

The above is just an example and may not work, do not use it.

Jim

---

### Post by Philio on 2008-11-29
If the correct files are located in /boot, running update-grup should do this automatically.

I have several OS installed on my desktop PC and a single /boot partition, Ubuntu picks up other OS kernels and ads them to the menu.lst whenver it does a kernel update (bit annoying as have to manually edit it every time and OS does a kernel update).

---

