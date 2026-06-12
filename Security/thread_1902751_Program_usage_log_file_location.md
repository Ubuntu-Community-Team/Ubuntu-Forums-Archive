---
title: "Program usage log file location?"
date: 2011-12-31
forum: Security
---

### Post by nabbit on 2011-12-31
Hi all!

I'm hoping you guys might be able to help - I'm trying to find out if Ubuntu has any sort of logging for programs used (either by your account, or others). I've been through the System Log Viewer, the /var/log/ files, but can't find anything. Am I missing something or does Ubuntu not have this sort of logging facility?

I know a ps will catch everything currently running, but I'm looking for historical logging/auditing on the system.

Thanks!

---

### Post by MG&amp;TL on 2011-12-31
IDK about programs in general, but you can see command-line programs used since about a month back with:

```
cd
cat .bash_history
```

---

### Post by Locke_99GS on 2012-01-02
Since there are so many ways to start a program, the program woulod have to handle logging on its own, like nearly every other program. (Even those that log to the system log do so on their own)

You could write a short wrapper script which would call the program and log it, and edit the xdg menu data for programs and ad the script in-front of the program to be ran. This may seem a bit hackish, though, compared to the methods desktop users are accustomed to.

I am unaware any any actual 3rd-party program that would log things of that sort - but I'm usually wrong.

---

### Post by nabbit on 2012-01-03
I guess I'm just too used to Windows logging/auditing - the key difference is that Linux doesn't really distinguish between a program executable and any other file. 

I've since been told that auditd can be used to set this up - basically you flag each executable file - when it's used, it'll appear in the audit.log

You can also use Zeitgeist with Activity Log to manage it,but I don't seem to be able to get it to work with programs, only documents/pics/videos/etc :(

---

