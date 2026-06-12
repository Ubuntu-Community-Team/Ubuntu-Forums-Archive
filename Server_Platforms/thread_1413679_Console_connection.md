---
title: "Console connection"
date: 2010-02-22
forum: Server Platforms
---

### Post by ZeldeR on 2010-02-22
Hello community, 

I have one little running server without VGA connection and no chance to look on the tty. Is it possible to look on tty over serial connection with a console cable? Or work over serial connection on tty terminal?

PC <--serial cable--> server

Thx. very much and sorry for my bad english;-)

---

### Post by Iowan on 2010-02-22
SSH is not an option?

---

### Post by ZeldeR on 2010-02-23
Normaly I use SSH to manage this server, but if I have some troubles on tty kernel panic or less problematic things... There should be some solution for serial?

---

### Post by KiLaHuRtZ on 2010-02-23
In GRUB, add this to you def-opts in '/boot/grub/menu.lst'...

```
# defoptions=console=ttyS0,9600n8
```

Update GRUB...

```
sudo update-grub
```

Then, create the file '/etc/event.d/ttyS0' and populate it with these lines...

```
start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/getty 9600 ttyS0
```

Reboot...done!

---

### Post by ZeldeR on 2010-02-23
thank you very much, it was very helpful :D

---

