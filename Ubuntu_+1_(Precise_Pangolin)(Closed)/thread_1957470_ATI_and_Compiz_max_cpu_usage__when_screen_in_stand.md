---
title: "ATI and Compiz max cpu usage  when screen in standby mode bug"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by georgelappies on 2012-04-12
Hi all

Does anybody else encounter the bug where if you use the drivers installed by Jockey and the screen goes into sleep (blacks out) that compiz then maxes one of the cores of the CPU?

I am running 12.04 on a Dell laptop with an ATI display. If I use the proprietary driver this happens as soon as the screen blacks out. This makes the laptop to become hot and noisy as well as the battery doesn't last.

The problem is that as soon as you move the mouse or press a key the screen comes on and then compiz usage returns to normal. The only way to verify this bug that I know of is to log in via ssh to the machine which screen has gone into standby mode and then run htop.

---

### Post by emarkay on 2012-04-12
Same thing as this thread maybe? 
[http://ubuntuforums.org/showthread.php?t=1957518](http://ubuntuforums.org/showthread.php?t=1957518)

---

### Post by georgelappies on 2012-04-13
> **emarkay said:**
> Same thing as this thread maybe? 
[http://ubuntuforums.org/showthread.php?t=1957518](http://ubuntuforums.org/showthread.php?t=1957518)

My issue started actually from about two weeks ago when I first installed 12.04. So I don't think it is related to the updates yesterday fortunatly or unfortunatly ;)

---

### Post by drumour on 2012-04-13
Same 100% cpu usage here when screen blanks and checking by ssh and using top or htop. 
Not updated for a few days so also unlikely to be related to other link re yesterdays updates, though I removed compiz-plugins-extra and rebooted just in case.

Edit 1
There is a launchpad bug report with info request from possibly similarly affected users here:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860)

Edit 2
Now marked as triaged.

Tad unrelated but -If ACPI 5.0 modules were backported into the current kernel from 3.3 mainline then at least my year old systems could finally suspend and this would be a non-issue...

---

### Post by georgelappies on 2012-04-24
Does anybody have any feedback on this?

---

### Post by Docaltmed on 2012-04-24
It's been happening to me on 11.10 for months.

I just never bothered about it, because until Catalyst 12.3, standby mode would cause a locked computer anyway.

Now it's getting to be a bit of a bother.

---

