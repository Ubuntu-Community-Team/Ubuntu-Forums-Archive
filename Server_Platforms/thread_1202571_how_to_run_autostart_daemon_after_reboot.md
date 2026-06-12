---
title: "how to run autostart daemon after reboot"
date: 2009-07-02
forum: Server Platforms
---

### Post by monkeyking on 2009-07-02
Hi
Untill the latest upgrade to 9.04 I had a daemon starting at each boot.
Now it doesnt happen anymore,
But I can still start it manually with
/etc/init.d/mon start

Has anyone any idea how to add make it start automaticcly

thanks in advance

---

### Post by credobyte on 2009-07-02
System -> Preferences -> Startup Programs ( */etc/init.d/mon* as a command ).

---

### Post by monkeyking on 2009-07-02
Thanks,
But do you know how to do it with no Xserver?

---

### Post by Denisiuk on 2010-01-28
Lord, I have 1.5 hours looking for how I add the server daemon to autostart, why everyone thinks that autostart needed only with X?

---

### Post by Kemon on 2010-01-28
```
sudo vim /etc/rc.local
```
Add the program before: exit 0.
Is that what you need?

---

### Post by monkeyking on 2010-02-26
thanks

---

### Post by [CPR]-AL.exe on 2010-07-07
Is there a way to run it without root rights?

---

### Post by kemra on 2010-07-07
> **'[CPR]-AL.exe said:**
> Is there a way to run it without root rights?

I don't currently have a Linux machine to hand, but if you go to System>Administration>Startup you can add things in there that you want to autostart but don't need root privaledges for.

---

### Post by [CPR]-AL.exe on 2010-07-07
I have no GUI. Thanx, i already solved it via crontab

---

