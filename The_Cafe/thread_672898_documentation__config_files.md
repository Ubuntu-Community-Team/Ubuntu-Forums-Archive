---
title: "documentation / config files"
date: 2008-01-20
forum: The Cafe
---

### Post by Vesslan on 2008-01-20
is it just me or does it seem like the solution to most ubuntu problems on this forum is to install various GUIs for everything?

coming from Arch i miss my rc.conf...  but i have no doubt that i will get used to the ubuntu way if only i can find my way around the config files.

so, i guess my question is, is there a reason that the official documentation don't include a guide to the most useful config files?

(maybe i just haven't been able to find the proper documentation, in that case please link to it?)

---

### Post by adamogardner on 2008-10-10
good question. I've been scouting around myself

---

### Post by koenn on 2008-10-10
> **Vesslan said:**
> is it just me or does it seem like the solution to most ubuntu problems on this forum is to install various GUIs for everything?

coming from Arch i miss my rc.conf...  but i have no doubt that i will get used to the ubuntu way if only i can find my way around the config files.

so, i guess my question is, is there a reason that the official documentation don't include a guide to the most useful config files?

(maybe i just haven't been able to find the proper documentation, in that case please link to it?)

I can't speak for Ubuntu/Canonical, but I assume the official reason is that Ubuntu is for human beings, and human beings should not be exposed to text configuration files, shells, or other instruments of torture from the 80's.

You'll find that most, if not all, config files live in /etc, usually with a reasonably recognizable name, eg /etc/samba/smb.conf is for ... samba !

There's one major exception to this : gnome uses a hierarchical structure of xml files that aren't meant to be human-readable, you use gconf-tool to get/set values from a shell, or use the GUI stuff. This goes for all things embedded in gnome desktop, panels, ...

Apart from that, reading up on Debian system administration (or just a user guide) will help you understand the inner workings of Ubuntu, cau'se they're pretty close. 1 notable exception is the use of sudo vs root logins, but that's documented in the Ubuntu Wiki. There may be a few other minor differences.

---

