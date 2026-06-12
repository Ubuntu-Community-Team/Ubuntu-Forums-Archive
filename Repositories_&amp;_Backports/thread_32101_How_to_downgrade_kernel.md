---
title: "How to downgrade kernel?"
date: 2005-05-06
forum: Repositories &amp; Backports
---

### Post by dierre on 2005-05-06
Hello!

I'm running ubuntu 5.04 and trying to make heartbeat work but I'm havin a lot of problems.

I've heard that downgrading to kernel version 2.4.x or 2.6.8/9 could help and I would like to try that... Unfortunately I cannot find any kernel image of such version. I've looked on packages.ubuntu.com and searched packeges.ubuntu.com but I cannot find anything suitable.

Am I doing something wrong or really there isn't anything like that? The latter sounds quite strange to me...

Thank you for your help!

Francesco

---

### Post by dierre on 2005-05-06
I shall answer myself: ;-)

On packages.ubuntu.com do a search for linux-image  (or 2.6.8 or something similar) and *don't forget to select "any distribution" *

Enjoy your day,

F.

---

### Post by trainrabbit on 2011-08-16
Instead of compiling it yourself and have to  build a god forsaken config file for the compilation, you can install a  linux-image package from the repositories. If you do a quick [LEFT]sudo aptitude search linux-image[/LEFT]
 [LEFT]You can see the fine result:[/LEFT]
 [LEFT]*p   linux-image-2.6.25-2-386 – Linux kernel image for version 2.6.25 on i386*[/LEFT]
 [LEFT]so if you install the package with[/LEFT]
 [LEFT]sudo aptitude install linux-image-2.6.25-2-386[/LEFT]
 [LEFT]You’re all set. The kernel will be automatically added to your grub menu.

[/LEFT]

---

### Post by garvinrick4 on 2011-08-16
This is one old, old thread!!

---

