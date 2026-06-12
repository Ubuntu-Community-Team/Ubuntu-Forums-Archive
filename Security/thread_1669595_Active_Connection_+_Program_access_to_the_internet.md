---
title: "Active Connection + Program access to the internet"
date: 2011-01-17
forum: Security
---

### Post by Alive01 on 2011-01-17
There is this active connection in firestarter: ec2-174-129-193-12.compute-1.amazonaws.com (Port 443 - Service HTTPS - program python)

After doing ps aux | grep PID it shows:  /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon

This comes up in the firewall in each login, how do I get rid of it and how did it get there in the first place?

Another question is if there is a way to limit a program's access to the internet. For example KCalender.. The things I type up in there may be stored somewhere. How can I disable complete access to the internet for that program and any other program so they can't backup, share, check etc. ?

---

### Post by mikewhatever on 2011-01-18
Open the list of startup applications and uncheck the 'Ubuntu One' entry.

There is no per-applicaton firewall in *buntu. I know nothing about "KCalender", but if it does something you don't want it to, just use another app.

---

### Post by Alive01 on 2011-01-18
> **mikewhatever said:**
> Open the list of startup applications and uncheck the 'Ubuntu One' entry.

I know nothing about "KCalender", but if it does something you don't want it to, just use another app.

KCalender isn't doing anything wrong, I just wanted to know if you can limit any kind of program.

---

### Post by DrFolger on 2011-01-19
Apparmor can limit specific programs from internet access, although it may not be the simplest or easiest method.

---

### Post by Alive01 on 2011-01-20
**Where is the startup applications manager in Kubuntu?**

---

