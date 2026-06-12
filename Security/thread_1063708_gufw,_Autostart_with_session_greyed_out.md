---
title: "gufw, Autostart with session greyed out?"
date: 2009-02-08
forum: Security
---

### Post by ucalagon on 2009-02-08
Have ubuntu 8.10. Seem to have to start gufw every session. Option to Autostart is greyed out in Preferences.  Am I doing something wrong?
All help welcome - David (refugee from Windoze Vasti)

---

### Post by hyper_ch on 2009-02-08
why do you want to start it with every session?

---

### Post by ajgreeny on 2009-02-08
gufw is not actually your firewall; that is iptables, and it runs all the time.  gufw is just the application you can use to make changes to the configuration.  It is an easy way to do it in terminal without the need for a bigger GUI application such as firestarter or guarddog.

---

### Post by ucalagon on 2009-02-09
> **ajgreeny said:**
> gufw is not actually your firewall; that is iptables, and it runs all the time.  gufw is just the application you can use to make changes to the configuration.  It is an easy way to do it in terminal without the need for a bigger GUI application such as firestarter or guarddog.
Thanks to both for help.  This next may belong in "desktop", if so, apologies.  When I chose "suspend" or "hibernate", I get total shutdown, no K/B or mouse response. Tower on/off quick press gives mobo restart but no return to ubuntu, just black screen. 
All help welcome - David

---

### Post by gaiterin on 2009-02-11
Hi!
Do you use Gnome?
Gufw will search the directory /home/user/.config/autostart ;)
If it not exist, Autostart will be not active.

When you install fresh installation, maybe not exist. This directory is used for autostart programs ;)

But the Gufw rules persists always in the system, because Gufw send the command to ufw, and ufw modify iptables. Then iptables persists the rules in all moment ;)

Autostart exist if you change the rules more times in a day ;)

Cheers!

---

