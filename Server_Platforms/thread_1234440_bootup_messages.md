---
title: "bootup messages"
date: 2009-08-07
forum: Server Platforms
---

### Post by boondocks on 2009-08-07
When the Ubuntu server boots up, I can see messages like:
...
Starting kernel ..... [ ok ]
...
Starting MySQL  ..... [ ok ]
...

This is good.  I want/need to see these messages.
But after everything has started, I want the console to do the equivalent of a "clear" and then display the login prompt.
I don't want the console to disclose any of the services that it is running.

In which file can I append something like this?
sleep 15
clear

So that it shows the tail end of the boot messages for 15 seconds and then clears the screen, then it displays the usual login prompt.

---

### Post by samosamo on 2009-08-07
I can't answer your question but maybe you might want to look at the grub option "quiet" (not the kernel option, the grub option).  Not sure how it behaves in ubuntu server edition though.

```
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

---

### Post by boondocks on 2009-08-07
> **samosamo said:**
>  ... maybe you might want to look at the grub option "quiet" (not the kernel option, the grub option).  

I tried that.  It did not help.
It still shows the tail end of the boot messages at the console.

---

