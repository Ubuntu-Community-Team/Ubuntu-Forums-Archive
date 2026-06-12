---
title: "remote ssh access not showing in last"
date: 2009-08-05
forum: Security
---

### Post by jamie1985 on 2009-08-05
Hi all, 

I am running 9.04 with SSH and Apache. There are 4 users on the system, with one of them being used for remote SSH Access (i.e. not from our internal network). 

Logins for this user are not appearing in last, lastlog or who, despite the user being logged in and having an active conenction in netstat -tunapl. 

I've logged on using the username in question localy, which appears in who, last and lastlog. 

Does anyone have any ideas why remote logons are not showing up? The connection is being routed from our firewall, and accessing the host via an external IP (as opposed to the hostname/internal IP).

Any help would be greatly appreciated.

Cheers,

J

---

### Post by configt on 2009-09-09
I am also having some issues with who and finger.

I have 2 users logged in, yet who and finger show nothing:

jbutler@newkid:~/Desktop$ who
jbutler@newkid:~/Desktop$ finger
No one logged on.
jbutler@newkid:~/Desktop$ 

last shows users still logged in, but who and finger show nothing.

That seems like a huge security risk.

Is anyone else having this problem?

---

### Post by configt on 2009-09-09
Weird.  Apparently I was missing /var/run/utmp.

Simply touching the file to create it solved the problem.

I just have to wonder, why was the file missing in the first place?

---

### Post by flugh on 2009-09-09
Not saying it's your problem, but I just read this thread:
[http://ubuntuforums.org/showthread.php?t=1260606](http://ubuntuforums.org/showthread.php?t=1260606)

Apparently there are ssh-related concerns afoot.

And utmp was probably missing because it showed someone logging in that that user didn't want you knowing was there. That would be my guess. Given the information in the other thread, which could probably be backed up with a few Google searches, I'd assume the machine was compromised, take it offline. That's just me, I'm no expert.

---

