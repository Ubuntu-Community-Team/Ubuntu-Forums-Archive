---
title: "Fresh LTSP install delivers initramfs"
date: 2010-03-02
forum: Server Platforms
---

### Post by ICEB3AR on 2010-03-02
Hi there,

I don't know, if I'm too stupid or if I can't see anything very obvious. 
I've installed LTSP-Server using 8.04.04 alternate on a System with One NIC (Configured Static: 192.168.0.1/255.255.255.0)
Everything fine. 

When i try to boot from network first everything seem to be fine. It gets a IP from network and loads the kernelimage and then the ubuntu boot screen appears for some seconds. But then there is only a shell:
```

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```

Shouldn't there be the login-Screen? Could that be caused by too old hardware? Or am I missing something? Sorry, but anyhow the documentation always says it's so simple. Install ltsp-server, Build image and you were able to boot...

By the way: Reboot doesn't help either.

Any help would be very appreciated.

---

### Post by nerr on 2010-03-02
I actually am encountering the same problem with my PXE box, so I'm going to drop a post here and follow this thread for advice. :)

---

### Post by ICEB3AR on 2010-03-02
I got a bit more Information about my Problem. When Trying to boot the following erros appear (Pressing CTRL + ALT + F1):

```

mount: Mounting /rofs on /root/rofs failed: Invalid argument
cp: unable to open '/root/etc/': Is a directory
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

```

I also found this thread: [http://ubuntuforums.org/showthread.php?t=686966]("http://ubuntuforums.org/showthread.php?t=686966")

I'm not able to rebuild the client at the moment, but will try. As it looks like in the thread this seem to help.

---

