---
title: "Booting Problems"
date: 2020-03-25
forum: Ubuntu/Debian BASED
---

### Post by ivan23m on 2020-03-25
Hello

I assume this isn't a Linux system problem per se, it's probably a hardware problem but I use Linux Zorin 12.4 which is based on Ubuntu 16.04 so I'm posting here. Yesterday when booting I got this message:

   ```
BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)  Enter 'help' for a list of built-in commands

   (initramfs)
```

I followed the advice [here,]("https://askubuntu.com/questions/741109/ubuntu-15-10-busybox-built-in-shell-initramfs-on-every-boot") typed exit then fsck /dev/sda1 and then reboot and everything was fine, PC booted. Later initfram message during boot showed up again (it also showed up once a few months ago, this was the third time),  I repeated the same procedure and everything was ok again.

Today again I got a number of messages while booting, this time more then yesterday. I restarted the computer a few times and it's working now but I'm assuming this will happen again. What exactly is going on?

And I apologize, some pictures are rotated, I don't know why that happened.

---

### Post by ivan23m on 2020-03-25
This is what showed up today.

---

### Post by ivan23m on 2020-04-03
I wrote this a week ago but there wasn't a response so I'm writing you a reminder.

---

### Post by CelticWarrior on 2020-04-03
Your drive is failing, that's all. Backup, replace it and reinstall.

---

