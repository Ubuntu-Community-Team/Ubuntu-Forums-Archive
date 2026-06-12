---
title: "&quot;CPU Frequency Montior&quot; and &quot;Mail Watcher&quot; issues"
date: 2012-10-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pqwoerituytrueiwoq on 2012-10-03
when you click on the "CPU Frequency Montior" you get a window designed to change the cpu goverenor
this applet used to ask for a password if you changed the setting, it no longer does

the "Mail Watcher" alerts you every time the number of unread messages changes
for example if i have 2 messages and i read one it plays the new mail sound
:idea: anyone have a conky script for gmail?

---

### Post by mc4man on 2012-10-03
> **pqwoerituytrueiwoq said:**
> when you click on the "CPU Frequency Montior" you get a window designed to change the cpu goverenor
this applet used to ask for a password if you changed the setting, it no longer does

Nothing new in Ubuntu, set in the .pkla in self explanatory screen, Xubuntu also has this .pkla

---

### Post by pqwoerituytrueiwoq on 2012-10-03
how does this file help?
```
/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```

---

### Post by mc4man on 2012-10-03
> **pqwoerituytrueiwoq said:**
> how does this file help?
```
/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```
'Help' may be relative to your pov

The section in the .pkla overrides the policykit default action in /usr/share/polkit-1/actions/org.gnome.cpufreqselector.policy - 
<allow_active>auth_admin_keep</allow_active>

with
ResultActive=yes
(for users in the admin or sudo group

( In a Ubuntu 12.10 install there are 2 actions so they've added a separate .pkla for the 
com.ubuntu.indicatorcpufreqselector.setfrequencyscaling one.

---

