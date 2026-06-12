---
title: "Server Goes Into Emergency Mode On Boot"
date: 2017-09-01
forum: Server Platforms
---

### Post by odonnell on 2017-09-01
I have a similar problem. If someone can just point out where to find the immediate cause of the failure, presumably in one of the many logs, that will be a huge help. The advice printed when emergency mode comes up has not been helpful.

I have been running Ubuntu Studio for years, and have updated to Zesty. I had apparently random incidents of booting into "emergency mode" for many months, but the problem recently began to happen on every startup.

* The restart performed by Software Updater succeeds.

* I can select the "upstart" option in the Grub "Advanced" submenu, leading to a mode with 5 pseudo ttys but no display manager runlevel=2. I can then start lightdm manually and get a very similar work environment to my usual, with some peculiar differences in DNS behavior.

* A default restart, which I understand uses systemd rather than upstart, always leads to the message "You are in emergency mode," and a bit later "Press Enter for maintenance."

* I keep 4 kernels, two versions in lowlatency and generic variants. I see no difference in behavior when I select different kernels.

* If I select the "recovery mode" option in the Grub "Advanced" submenu, I eventually reach a state with the display manager, and I can log in to an X session, but the graphics resolution and aspect ratio are wrong. The "upstart" option has been more helpful, so I haven't explored recovery mode further.

I can't imagine that anyone can diagnose the problem from this information, but if someone can just point me to the right sort of entry to search for in the right log, I think that I can make progress.

Thanks,

Mike O'Donnell

---

### Post by odonnell on 2017-09-04
I solved my problem, and mooted the question for my immediate purposes, by reinstalling from a Xubuntu USB stick. It was a sensible step after years with an accumulation of minor problems.

It would still be great to know how to find the reason for Emergency Mode. I searched /var/log files and config files without finding a clue that I could recognize.

Cheers,

Mike O'Donnell

---

