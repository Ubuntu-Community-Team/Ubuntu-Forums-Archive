---
title: "&quot;shutdown now&quot; does not shutdown"
date: 2010-03-06
forum: Server Platforms
---

### Post by qajaq on 2010-03-06
I've just installed the Ubuntu server 9.10. At one point in the course of configuring it, I decided to change the hardware on the machine, so I gave the command ```
# shutdown now
```
The system issues a notice that it's going down for maintenance NOW! Then it displays a series of notices about what processes it's stopping, and finally it offers a menu that looks something like this: 
> [FONT="Courier New"]
clean    Try to make free space
dpkg     Repair broken packages
grub     Update grub bootloader
netroot  Drop to root shell prompt with networking
root     Drop to root shell prompt

<OK>                  <Cancel>[/FONT]

No matter which option I choose, the machine does not shut down. Eventually, every option leads to a reboot.

I've noticed this problem, too, when using the "shutdown now" command from the CLI in desktop versions (I've used 8.10 and 9.04), but I was always able to get around it by using the GUI shutdown button. But since the server version does not have a GUI, it's time for me to learn what's going on and how to make it different.

How do I shut down an Ubuntu machine from the CLI?

---

### Post by cgroza on 2010-03-06
The right command is " shutdown -h now " , your command shuts down the system but it does not halt it.

---

### Post by lavy on 2010-03-06
I don't know the problem but you might find a workaround using halt command.

---

### Post by lavy on 2010-03-06
> **cgroza said:**
> The right command is " shutdown -h now " , your command shuts down the system but it does not halt it.

Yes you are right I haven't notice that :)

---

### Post by qajaq on 2010-03-06
Thanks, both of you. On my system, the -h argument didn't do what I wanted, but using your clue, I read the man-page and found that the -P argument is what does it.

---

### Post by NullHead on 2010-03-06
If you're not doing this with ssh remote, you could always hard-off it with the sysrq key. It's a bit oldschool, but it works. :popcorn:

---

### Post by qajaq on 2010-03-06
Yeah, Nullhead, I did that in order to shut down last night, but I was looking for the more elegant solution -- which was provided here. One of the things I love most about Linux and FOSS is the free sharing of expertise. Thanks!

---

