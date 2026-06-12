---
title: "Can't boot unless legacy mode is enabled"
date: 2014-12-27
forum: Ubuntu/Debian BASED
---

### Post by newbie13 on 2014-12-27
I have installed latest Kali Linux on my laptop along side ubuntu and win8.

When I turn on legacy mode (which enables running older OS) then I am able into boot into Kali but when it is off, after selecting Kali from grub menu, blank screen appears with white blinking cursor on upper left corner. I tried installing in UEFI mode as well as normal mode but both the times same thing happened. I have to keep legacy mode on to use Kali. Ubuntu does not face this problem.

One good thing is, when that blank screen appears I can press Alt+F2 or F1 to bring log in menu in terminal like environment and use all the commands, but unfortunately I am not much familiar with terminal.

So what should I do?

I am going to try installing it again in both modes till then, certainly, someone would have suggested something

---

### Post by ajgreeny on 2014-12-27
Are Win 8 and Ubuntu installed in UEFI mode?

If they are you _*must*_ install kali in UEFI in order to be able to boot to all your OSs; you can not mix the two modes successfully as it would involve changing the boot mode from UEFI to legacy each time you needed to move from an OS in one mode to another OS in the other mode.

Let's see the output of Boot-Repair in my signature; just show us the pastebin link it gives you in your reply.  That may tell us exactly what has gone wrong.

---

### Post by newbie13 on 2014-12-28
It was my fault.
I had installed it keeping legacy mode on everytime and to boot it, when legacy mode is on, I had to add radeon.modeset=0. But when I turn legacy mode off, as it turns out, there is no need to add that line.

The same thing which was helping me to boot, now, was preventing me from booting.. lol..

(out of the topic- I just completed reading shiva trilogy by amish, whose basic theme is that the greatest good will some day turn into the greatest evil and shiva, who is destroyer of evil, will come and take that evil out of the equation until it is required again. Obviously that radeon.xxxx line was not anyhow the greatest good nor shiva came to me to tell me the solution but it felt nice to see that theory in practical)

Thank you ajgreeny and this forum

---

