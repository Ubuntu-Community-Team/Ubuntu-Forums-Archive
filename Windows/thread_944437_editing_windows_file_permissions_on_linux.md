---
title: "editing windows file permissions on linux"
date: 2008-10-11
forum: Windows
---

### Post by HungryMan on 2008-10-11
Last march, I ran a program that I thought was an installer of a certain program. Suddenly, My wallpaper disappeared, pop-ups pop-upped my start menu acted weird, it was a virus (virii actually). Quickly, I rebooted into safe mode, ran security task manager and looked for suspicious processes. I restricted access to them (I'm not sure if the file is important). One of them was msgina.dll

Here comes my question, how can I undo what I have done? The file was on an NTFS partition and I removed all permissions to all users. I had simple file sharing turned off. I have no problem on ubuntu, it's just that Windows XP itself can not access msgina.dll. I am not interested in any antivirus software, as I am quite sure that no further damage can be done. By permissions I do not mean chmod permissions on unix-based systems.
Any help is appreciated.

---

### Post by Izek on 2008-10-17
Run CACLS in cmd / command prompt as an admin in Windows. Unless you can't get into windows. (If you can't get into windows, then this should be moved.)

[http://www.ss64.com/nt/cacls.html](http://www.ss64.com/nt/cacls.html)

Or do you mean login permissions?

---

### Post by HungryMan on 2008-10-20
nope, I meant the permissions in the right click>properties>security  but AFAIK this only works on an NTFS volume with simple file sharing turned off.
I'll post a screenshot if I get to use windows again.

---

