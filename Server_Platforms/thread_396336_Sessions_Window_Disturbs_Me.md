---
title: "Sessions Window Disturbs Me"
date: 2007-03-29
forum: Server Platforms
---

### Post by tonyr1988 on 2007-03-29
System >> Preferences >> Sessions

Why does that not require root access to edit? I'm sure that it's got something to do with it editing a config. file in my ~ directory, and it makes perfect sense, but the fact that a program (or person) can edit my startup programs without going through sudo (or gksudo) unnerves me.

I remember when I used WinXP (what a dark time in my life...:D), that was the most annoying part - malware infecting your startup programs. 

Is there any chance that this could be changed in future releases, or is it too difficult to do (or is there a good reason justifying it)? Is there a way that I could personally change things to accomplish what I want? I don't want to start messing with chmod'ing config files when I don't know what I'm doing.

Thanks a ton everyone

---

### Post by yabbadabbadont on 2007-03-29
Either log out or lock your screen when you are away.  Anything more is overkill as anyone who has physical access to the machine can (if they try hard enough) do anything they like to it.

---

### Post by tonyr1988 on 2007-03-29
I completely agree with that - all they have to do is boot in recovery mode and they have root access to everything (unless that's changed, which I don't think it has).

I was mainly talking about remote access. I thought the main point of requiring root / sudo on certain operations was to prevent someone who managed to get remote access from destroying lots of things (or limit the damage of unruly applications). I just don't see why the startup program list isn't protected, or if there's a way I can change that.

---

### Post by yabbadabbadont on 2007-03-29
If they have compromised your account remotely, it is only the files to which you have access that will be affected.  That includes the startup programs.  It won't affect the rest of the system.  (at least the parts that require sudo)  If they have breached your account once, odds are the can do it again.  Besides, why would they assume that you are using Gnome for their exploit?  They could just as easily replace your ~/.profile ~/.bashrc ~/.bash_profile ...

---

