---
title: "Grub booting windows11 into sleep mode"
date: 2022-11-01
forum: Windows
---

### Post by dotborg2 on 2022-11-01
Hi all,
 I've just installed ubuntu 22.04 as dual boot on a windows 11 NUC and now selecting windows boot loader from the grub menu sends the box to sleep. I need to press the power button twice (once off and once on) before it will display the windows log-on screen. (Note - it doesn't reboot here, it just wakes up).
 Windows will boot fine if selected to be first in my bios (i.e - launching the windows boot manager and not grub), so I'm guessing it's a grub issue.
I have the option of adding ubuntu to the windows boot loader and using that instead, but it would be nice if I could get grub working.
 Does anyone have any ideas where I could start looking please? My web searches have come up blank so far.

Thanks in advance

---

### Post by yancek on 2022-11-01
You could try turning off Secure Boot and hibernation in windows to see if that resolves the problem.

---

### Post by dotborg2 on 2022-11-02
All the windows sleep options are off, secure boot and fast boot are also already off - these have no effect.
Interestingly, if I select the windows option in Grub and hit 'e' to bring up the edit screen, I can then just continue to boot into windows from there and it loads fine. 
There's just something odd happening with the initial Grub menu.

---

### Post by tea for one on 2022-11-02
> **dotborg2 said:**
> Interestingly, if I select the windows option in Grub and hit 'e' to bring up the edit screen, I can then just continue to boot into windows from there and it loads fine.
That's a bit unusual.
I would boot into Ubuntu and run:-
```
sudo update-grub
```
Make sure that you have this entry in etc/default/grub
```
GRUB_DISABLE_OS_PROBER=false
```
Any improvement?

---

### Post by dotborg2 on 2022-11-02
No luck with those either I'm afraid, I'm suspecting a hardware issue now to be honest. With a bit of luck I can still exchange it.
The help is much appreciated anyway.
Thanks to all.

---

### Post by danial62 on 2023-03-11
[COLOR=#000000][INDENT]You should turn off Secure Boot in windows and give it a try. Who know if this work for you. [https://thedigitalbin.com]("http://thedigitalbin.com/")[/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by dotborg2 on 2023-03-13
This ended up being a hardware issue and was resolved with a fix from the manufacturer (an issue with the hdmi ports..). Thanks all anyway.

---

