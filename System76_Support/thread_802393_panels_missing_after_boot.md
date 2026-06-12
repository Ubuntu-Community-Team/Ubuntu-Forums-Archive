---
title: "panels missing after boot"
date: 2008-05-21
forum: System76 Support
---

### Post by gruntlips_ on 2008-05-21
I solved this but of course I cannot figure out how to delete this posting.

---

### Post by Vadi on 2008-05-21
Don't! Say instead how did you solve it. So others that'll have the same problem later might find this solution.

---

### Post by gruntlips_ on 2008-05-22
Sure. I hit ctrl-alt-F2 and typed:

sudo apt-get install gnome-desktop

ctrl-alt-F6 to return to the dekstop

rebooted

It did not like the the trash or volume control applets so I went to a terminal and typed:

sudo apt-get install gnome-applets

rebooted

Actually I had to reboot, twice more.  The first time it installed the trash several times. I removed it, cursed, and restarted, and now it works fine.

---

### Post by MorphWVUtuba on 2008-05-22
> **gruntlips_ said:**
> Sure. I hit ctrl-alt-F2 and typed:

sudo apt-get install gnome-desktop

ctrl-alt-F6 to return to the dekstop

rebooted

It did not like the the trash or volume control applets so I went to a terminal and typed:

sudo apt-get install gnome-applets

rebooted

Actually I had to reboot, twice more.  The first time it installed the trash several times. I removed it, [COLOR="Red"]**cursed**[/COLOR], and restarted, and now it works fine.

AHA!  So THAT'S how you fix it.:lolflag:

I use that daily at my helpdesk job.

---

