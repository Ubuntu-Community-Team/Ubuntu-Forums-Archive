---
title: "can't boot with splash after upgrade to Hardy Heron"
date: 2008-06-24
forum: Server Platforms
---

### Post by biocyberman on 2008-06-24
Hello,
After upgrading to Hardy Heron I couldn't boot to newer server kernel. After new kernel from boot menu. The screen became black out like it's turned off ans stayed like that forever. I could hit "Ctrl + Alt + Del+ to restart the server though. After pulling my hair for a while I was able to boot in to recovery mode and chose "resume to normal boot" and I could boot into my server. I found that the only difference between recovery mode and normal mode is the "spash" parameter so I removed it as following:

This is a section in my /boot/grub/menu.lst: 

```

title		Ubuntu 8.04, kernel 2.6.24-19-server
root		(hd0,0)
#kernel		/vmlinuz-2.6.24-19-server root=/dev/mapper/myserver-boot ro quiet splash
kernel		/vmlinuz-2.6.24-19-server root=/dev/mapper/myserver-boot ro quiet 
initrd		/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-server (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-server root=/dev/mapper/myserver-boot ro single
initrd		/initrd.img-2.6.24-19-server

```

After that I am able to boot with no problem. I got my login screen and came in gnome normally. So what's wrong with the splash parameter.
 
I am running HP Proliant wiht 1 Intel QuadCore 1.6Ghz and Ubuntu Hardy Heron Server 86_64 (upgraded from Gutsy) with ubuntu-destop installed.

Thanks for any response.

---

### Post by windependence on 2008-06-24
Just a guess but I'm thinking the splash screen file has been moved or is in a different location and the bootloader couuld not find it.

-Tim

---

### Post by biocyberman on 2008-06-25
@Tim: When booting into old kernel, I still see the splash screen. I don't know if the default splash screens of old and new kernel are put at different locations.

---

