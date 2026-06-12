---
title: "Compiz uses a lot of CPU when there is an unresponsive window"
date: 2013-02-27
forum: Ubuntu Development Version
---

### Post by Lisiano on 2013-02-27
Yesterday I installed Raring on my netbook and for some reason, whenever there is any unresponsive window, the cpu usage raises to 50%-80%. Not sure if this is Raring specific as I haven't got a chance to test this on my desktop running Quantal. Beside decreasing the icon size of Unity icons, no tweaks related to Compiz or Unity were made.
So, anyone else experiencing this?

---

### Post by grahammechanical on 2013-02-27
How do you know that the issue is with Compiz. When I open a 600+ page Libreoffice Writer doc, the window greys out. But running Top shows that Compiz does not go above 3% CPU usage and 7% memory usage (out of 1GB). whereas soffice.bin is using 99% CPU. Compiz soon drops CPU and Memory usage even lower.

There has been much improvement in regard to memory usage in 13.04 due to the work done on Ubuntu phone. But, no, I do not see Compiz eating the CPU.

Regards.

---

### Post by Lisiano on 2013-02-27
Exactly that way, I used top and the Compiz line showed above 50% usage. I'll try to get something to hang up to get a screenshot.
EDIT: Told Skype to load the whole history of a group chat (It contains a TON of messages). Before the window got greyed out, compiz was bellow 10%, after it greyed out, it raised to 70%-90%.
[IMG]http://ubuntuone.com/6kqTZ1KPPpt8Me2zeHImS6[/IMG]
Note: In that screenshot it's Skype that became unresponsive (Well... Was forced to become unresponsive) but it happens with every window that becomes unresponsive, like Chrome, Synaptic, Empathy, even a Terminal if there is a lot of stuff running.

---

### Post by williejones on 2013-02-27
The top usage is showing 97 for skype and 87 for compiz.  This is over 100% ?????????

---

### Post by cariboo on 2013-02-27
Depending on how many cores your cpu has, usage will show for each individual core.

---

### Post by stoneguy on 2013-03-08
This was pretty dire when there's a single core (my Celeron 900 netbook). The past couple of days' updates seem to have fixed it.

---

