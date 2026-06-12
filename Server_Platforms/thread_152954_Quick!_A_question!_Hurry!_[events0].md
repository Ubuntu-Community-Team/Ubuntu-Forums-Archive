---
title: "Quick! A question! Hurry! [events/0]"
date: 2006-03-30
forum: Server Platforms
---

### Post by LadyDoor on 2006-03-30
Ok, so...

I'm on my computer and all of a sudden everything starts going soooooo slowly. Now, I'm using Ratpoison window manager right now, with not a lot of programs running, and with anything this bare it's stupid that anything would go slowly. So anyways I do top and see some action supposedly started by root that's taking up anywhere from 50-89% of my memory, called [events/0]. So, figuring it would run its course, I left for a while as I had been about to do anyway. 

So I come back 2 hours later, and it's still going! So...I run clamscan (the latest version with the latest virus definitions) and rkhunter, and find nothing (except for some files marked as "suspicious" because of their dots--/dev/.static, which contains another directory called dev; /dev/.udevdb; /dev/.initramfs-tools, which is an empty file; /etc/.pwd.lock, also empty; and /etc/.java, which contains a directory called .systemPrefs containing two empty files--if any of these are evil, please let me know!).

I also ran Top with the command to get it to show me the command lines for each program running instead of its name, and [events/0] is apparently just that. So I search for it using locate, which, whereis, whatis, etc., but find no evidence of it on my computer except for the fact that Top says it's taking up like all of my memory all of a sudden and has been for two hours. Does anybody know whether this is a Very Bad Thing, or just some stupid thing I could, like go all **sudo kill** on and be able to use my computer right? Any help is much appreciated.

Thanks in advance,
Door

---

### Post by LadyDoor on 2006-03-31
Well, I left and read for a while and came back. I searched for just events, and figure that it probably has something to do with power management gone mad, since it there was an events dir in /etc/acpi, and when I **man**ned acpi it said it was for power management, and then when I experimentally unplugged my laptop X basically froze up (but I could get to a console w/o X--CTRL+ALT+F1), but couldn't kill the process--it was one of those things that for some reason claims to be successfully killed but actually still going, the dirty liar. Soooo, I restarted my computer and the problem resolved itself--I just wish I knew what caused it to go haywire and take up all those resources in the first place! Could it be a security problem, or just a bizarre malfunction?

Anyway...
--Door

---

### Post by RavenOfOdin on 2006-03-31
[QUOTE=LadyDoor]and rkhunter, and find nothing (except for some files marked as "suspicious" because of their dots--/dev/.static, which contains another directory called dev; /dev/.udevdb; /dev/.initramfs-tools, which is an empty file; /etc/.pwd.lock, also empty; and /etc/.java, which contains a directory called .systemPrefs containing two empty files--if any of these are evil, please let me know!).[/QUOTE]

rkhunter does that to me too.
I think the first four of those are false positives.

Couldn't help ya with /etc/.java, though.

---

