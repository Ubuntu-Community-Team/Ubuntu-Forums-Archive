---
title: "xserver randomly freeze"
date: 2009-01-15
forum: System76 Support
---

### Post by mikhmv on 2009-01-15
Hi. 
I have installed Ubuntu Jaunty 9.04 64bit and now xserver regularly freeze. It is happen 8-10 times per day. 
I tried to feel bug but received reply only once.
Bug thread here: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/316566](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/316566)



Binary package hint: xorg

Hi,
I am just start work with linux and can not sure tell in which package bug.

Symptoms:
Xserver randomly freeze. Today it was frozen 5 or 6 times. It can happened in different situations. Some of them:
1) Working with Firefox
2) using Nautilus
3) resizing some windows
4) changing workspace
5) computer try to Sleep.

When System freeze usually mouse continue respond but some times disappear.

In all cases Combination keys:
1) Cntrl+Alt + RSEIUB work normally.
2) Cntrl+Alt+Backspase doesn't work but when system wasn't freeze this combination work good

Please help me resolve this problem.

---

### Post by thomasaaron on 2009-01-16
We won't be supporting 9.04 until it is officially released.

---

### Post by Lee_Machine on 2009-01-16
The nvidia drivers binaries are not support nor work at near stable levels with the new xorg. 

See the ubuntu developer wiki.

[https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview](https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview)

There is a work around. 

Do you have a S76 computer?
Which Alpha are you testing? I tried out Alpha 3 to see if the boot times with ext4 were as fast as the benchmarks I have been reading. On a older computer I got 24.2 seconds. Im looking forward to Jaunty  in April!

Doing a ctrl-alt-backspace to kill your x-session and reload a new one will not work in Jaunty. It has been disabled by default because many users invoke it on accident. I myself have. With more and more people coming from windows its a common issue. To enable it go to keyboard shortcuts, its been added there.

---

### Post by mikhmv on 2009-01-16
I am using Alpha 2 but with all updates. 
My video card is Intell ... X4500HD
I enabled ctrl-alt-backspace. Now it is work in normal working but don't work after freezing.
I am using Lenovo T500 notebook with 64bit linux

---

