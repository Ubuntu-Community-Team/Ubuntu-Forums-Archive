---
title: "Need advice on what to do after being cracked"
date: 2008-01-25
forum: Server Platforms
---

### Post by zuidema on 2008-01-25
All of a sudden things on my panels disappeared, after looking around for awhile I discovered a new user on my system. Went into users and groups and deleted the new user. Need to know what else I can do short of new install to insure that nothing else is lurking around. Rkhunter showed no rootkits but a lot of warnings about about hidden files and directories. Another thing I need to know is how to set system so  I don't have root account as it appears I have one. I have already changed my root password. (Thanks in advance)

---

### Post by PilotJLR on 2008-01-25
What was this username? Just want to make sure its not an account associated with a software package you installed.

Is the machine running ssh? Or apache? Or ANY servers at all?


These questions are meant to help figure out if you were really hacked. If you WERE hacked, then the only safe solution is a reformat and clean install.

---

### Post by zuidema on 2008-01-26
> **PilotJLR said:**
> What was this username? Just want to make sure its not an account associated with a software package you installed.

Is the machine running ssh? Or apache? Or ANY servers at all?


These questions are meant to help figure out if you were really hacked. If you WERE hacked, then the only safe solution is a reformat and clean install.
The user name was something like sobanon. No servers installed

---

### Post by p_quarles on 2008-01-26
> **zuidema said:**
> The user name was something like sobanon. No servers installed
The username "sobanon" doesn't sound like any standard system account, so that's definitely suspicious. Because you deleted the user, though, it would be difficult to know what level of access it had, and consequently difficult to know if you were compromised. 

I agree with PilotJLR: the only safe solution here is to do a clean installation.

---

