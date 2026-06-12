---
title: "Sudo Vulnerabilities!"
date: 2010-03-01
forum: The Cafe
---

### Post by MasterNetra on 2010-03-01
> 
...

In general, a standard system upgrade is sufficient to effect the necessary changes. Details follow: It was discovered that sudo did not properly validate the path for the ’sudoedit’ pseudo-command. A local attacker could exploit this to execute arbitrary code as root if sudo was configured to allow the attacker to use sudoedit. The sudoedit pseudo-command is not used in the default installation of Ubuntu. (CVE-2010-0426) It was discovered that sudo did not reset group permissions when the ‘runas_default’ configuration option was used. A local attacker could exploit this to escalate group privileges if sudo was configured to allow the attacker to run commands under the runas_default account. The runas_default configuration option is not used in the default installation of Ubuntu. This issue affected Ubuntu 8.04 LTS, 8.10 and 9.04. (CVE-2010-0427)
...



From: [http://www.ubuntugeek.com/sudo-vulnerabilities.html](http://www.ubuntugeek.com/sudo-vulnerabilities.html)

---

### Post by Redache on 2010-03-01
If it was a bug that's been fixed then it's not really a problem anymore as I'd hope that everyone who has Ubuntu installed automatically accepts updates.

---

### Post by jwbrase on 2010-03-01
I noticed that my machine performed a sudo update a few days ago, probably related.

---

### Post by t0p on 2010-03-01
Yesterday, Update Manager on my Hardy machine sent me a security update for *sudo*.  I assume the update was to deal with this issue? I also assume that computers running other versions of ubuntu also got a *sudo* update.  

Sorry, i don't understand the point of the OP.  Is it just to tell us that the recent security update was necessary to ensure security?  Cos I think I got that anyway.

But from the way this thread is titled - "Sudo Vulnerabilities!" with that dramatic exclamation mark!! - I get the idea that the original poster is trying to say "OMG a problem with *sudo*!  But the Ubuntu devs try to tell us that the *sudo* model is really secure!  So *sudo* isn't secure at all, we might as well all run as root all the time!!"

Or what?

---

### Post by Bachstelze on 2010-03-01
> **t0p said:**
> 
Sorry, i don't understand the point of the OP.

Probably because there is none.

---

### Post by doas777 on 2010-03-01
> **t0p said:**
> 
Sorry, i don't understand the point of the OP.  Is it just to tell us that the recent security update was necessary to ensure security?  Cos I think I got that anyway.

notification is most of the point of a security advisory. yeah, most of us have autoupdate on, and whatnot, but it is good to get the word out, especially regarding an priv escalation bug in the standard priv escalation mechanism. 

it has been a while since I logged into a couple of my servers.... I should probably check on them.

---

### Post by FuturePilot on 2010-03-01
Fixed awhile ago
```
sudo (1.7.0-1ubuntu2.1) karmic-security; urgency=low

  * SECURITY UPDATE: properly verify path for the 'sudoedit' pseudo-command
    in match.c
    - http://sudo.ws/repos/sudo/rev/88f3181692fe
    - CVE-2010-0426
```

---

### Post by t0p on 2010-03-01
> **doas777 said:**
> notification is most of the point of a security advisory. yeah, most of us have autoupdate on, and whatnot, but it is good to get the word out, especially regarding an priv escalation bug in the standard priv escalation mechanism. 


You're right, of course.  It's always good to know that there's a possible vulnerability that an update is available to address.  I just got the impression that the OP was saying "So *sudo* isn't the wonderful security feature it's been sold as at all! Hah!"  But that probably says more about me than the OP.

Still, in defence of *sudo*, I think it's worth repeating that this vulnerability can be exploited only by a *local* attacker - ie, someone who has physical access to the computer.  And it is generally accepted that if an attacker actually has his hands on the computer, it's just a matter of time before he owns the machine.

---

### Post by aysiu on 2010-03-01
Since this has an alarmist thread title and the flaw appears to be fixed, I don't see the point in this thread continuing.

---

