---
title: "Security help."
date: 2006-12-29
forum: Server Platforms
---

### Post by ftw_59 on 2006-12-29
I got a threat recently from an angry bigot that I pissed off who claims he's going to hack me and put questionable files on my computer then contact the FBI >_>; First off I know the odds of this happening are pretty slim, because nobody in their right mind would actually threaten to do it before they did it. But what can I use to keep an eye on my system to make sure he's not actually getting into it or something D:

---

### Post by EZ-man on 2006-12-29
Have you looked into Firewall Builder (iptables).

EZ :D

---

### Post by ftw_59 on 2006-12-29
I installed firestarter just to be safe. ;o

---

### Post by az on 2006-12-29
> **ftw_59 said:**
>  But what can I use to keep an eye on my system to make sure he's not actually getting into it or something D:

Pick a strong password.  Don't run services that you don't need (for example, ssh).   Keep up-to-date with software updates.

Don't run a proprietary OS.

Create a honey-pot and let him try to hack into it.  Show the logs to the cops.

---

### Post by johnnymac on 2006-12-29
Previous post is a good one...some other suggestions

1.  Use a route (it does a friggin awesome job and NAT protection)
2.  Using firestarter is a good thing
3.  Use an anti-virus (some will say it's not necessary but doesn't hurt)
4.  Install and use a root-kit hunter like chkrootkit to look for possible root-kits
5.  Monitor dmesg. /var/log/messages for weird info regarding attempted logins etc.
6.  If your REALLY paranoid you can run an IDS between your system and the internet (Intrusion Detection System).

GL -

---

### Post by ftw_59 on 2006-12-30
> **azz said:**
> Pick a strong password.  Don't run services that you don't need (for example, ssh).   Keep up-to-date with software updates.

Don't run a proprietary OS.

Create a honey-pot and let him try to hack into it.  Show the logs to the cops.

If he tries anything it will show up in the system log right? Do I keep an eye under messages? Because I was checking that pretty often before I installed firestarter.

---

