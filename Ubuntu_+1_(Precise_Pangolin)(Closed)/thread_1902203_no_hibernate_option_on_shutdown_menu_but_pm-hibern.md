---
title: "no hibernate option on shutdown menu but pm-hibernate works"
date: 2011-12-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2011-12-30
Hello All

I'm on 12.04 with unity 2d. Hibernate option not listed in the shutdown menu, but sudo pm-hibernate seems to be working fine and system seems to restore itself fine when powering up subsequently.

[LIST]
[*]Cosmetic issue with the menu?
[*]A bug in whatever checks if swap available for hibernating?
[*]A deliberate modification during testing incase pm system breaks?
[/LIST]

---

### Post by shubham1 on 2011-12-30
> **keithpeter said:**
> Hello All

I'm on 12.04 with unity 2d. Hibernate option not listed in the shutdown menu, but sudo pm-hibernate seems to be working fine and system seems to restore itself fine when powering up subsequently.

[LIST]
[*]Cosmetic issue with the menu?
[*]A bug in whatever checks if swap available for hibernating?
[*]A deliberate modification during testing incase pm system breaks?
[/LIST]

 itrhink there is no hibernate button in 12.04 as it is in cureently beta state i also have no hibernate button

---

### Post by keithpeter on 2011-12-31
Hello shubham1 and all

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/910183](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/910183)

If you

[LIST=1]
[*]Could see the hibernate option in 11.10 or other Ubuntu
[*]AND can't see the hibernate function in 12.04 on the same hardware with similar partitions
[/LIST]

could you add yourselves to this bug. I'm not convinced its Unity as such.

I think it may be the sub-system that tells Unity what options to include on the menu, but I had no clue as to the package name for that.

---

### Post by shoo_ash on 2012-01-15
Joined "this bug also affects me" club.
It can also be a policy privileges problem that tells the system it shouldn't enable hibernate for users.

> **keithpeter said:**
> Hello shubham1 and all

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/910183](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/910183)

If you

[LIST=1]
[*]Could see the hibernate option in 11.10 or other Ubuntu
[*]AND can't see the hibernate function in 12.04 on the same hardware with similar partitions
[/LIST]

could you add yourselves to this bug. I'm not convinced its Unity as such.

I think it may be the sub-system that tells Unity what options to include on the menu, but I had no clue as to the package name for that.

---

### Post by keithpeter on 2012-01-15
> **shoo_ash said:**
> Joined "this bug also affects me" club.
It can also be a policy privileges problem that tells the system it shouldn't enable hibernate for users.

Thanks for this suggestion shoo_ash and I'm googling all that now. Looks complex. 

I should say that Suspend is present as a shutdown menu option and works fine. Command supplied by pm-suspend, so that bit has permissions.

---

### Post by bcbc on 2012-01-29
Workaround: [http://askubuntu.com/questions/94754/how-to-modify-policykit-to-allow-hibernation-in-upower](http://askubuntu.com/questions/94754/how-to-modify-policykit-to-allow-hibernation-in-upower)

---

### Post by keithpeter on 2012-01-29
Hello bcbc

Well done, and I just had an e-mail from the bug page as well. I have modified the appropriate policy file and I now have a hibernate function visible in the Unity Settings menu.

Gnome Shell has an extension at

[https://extensions.gnome.org/extension/5/alternative-status-menu/](https://extensions.gnome.org/extension/5/alternative-status-menu/)

which a number of distributions are providing by default.

---

### Post by fabricator4 on 2012-01-29
I've added a 'me too' to the bug report.  The workaround given puts it back on the menu and is simple.  

Thanks

---

