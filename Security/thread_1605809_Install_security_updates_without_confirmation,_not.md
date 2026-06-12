---
title: "Install security updates without confirmation, not installing"
date: 2010-10-25
forum: Security
---

### Post by kainalu on 2010-10-25
With an Ubuntu 10.10 upgraded from 10.04, under Software Sources, Updates, there is a radio button marked "Install security updates without confirmation." I have this radio button marked, but still get "Important security updates" almost daily in my update manager. I don't remember this feature actually ever working. Any idea why?

---

### Post by kainalu on 2010-10-28
No one? OK, I'll file it as a security bug.

---

### Post by kainalu on 2010-11-10
Out of the whole Ubuntu Community, no one has heard of this bug, has a solution, or anything I can try or check? Absolutely No one? 

This kind of bug would have even got at least a little scrutiny on WINDOWS forums... I'm almost embarrassed that the security conscious Linux Community that I call myself a member of wouldn't even have a vague suggestion for me to try.

---

### Post by cariboo on 2010-11-10
What sort of behavior do you expect? Have you checked the [USN]("http://www.ubuntu.com/usn") against the packages on your system to see if they've been updated?

---

### Post by kainalu on 2010-11-10
I looked at the USN that you pointed to, and did a search, but I do not see the Update-Manager listed there at all. I have the button
"Install security updates without confirmation" marked in the settings, and the OS does download all updates, but the security updates don't get automatically installed like the settings indicate. They just stay available in Update Manager.

---

### Post by cariboo on 2010-11-11
I'm running natty (11.04), I manually update at least 3 times a day, so I can't check if the security updates get installed on my system.

Have you searched [https://bugs.launchpad.net]("https://bugs.launchpad.net") to see if there are any relevant bugs?

---

### Post by CharlesA on 2010-11-11
Do you have a link to the bug report?

I have mine set to install security updates automatically, but I haven't really been prompted to use update manager in 10.10.

---

### Post by kainalu on 2010-11-12
This is the bug report that I have created on LP.


[https://bugs.launchpad.net/bugs/668077](https://bugs.launchpad.net/bugs/668077)

---

### Post by kainalu on 2010-11-29
My updates still aren't installing, and this (in my opinion)leaves me vulnerable from a security standpoint, although the Ubuntu bug squad seems to disagree. I do not have daily access to this machine, to do it myself, which made the auto-install feature nice. it seems there is nothing stopping it from working but the OS itself. I suppose I could come up with some convoluted CRON job to replace the OS's update feature.

Or maybe there is an OS that can update on it's own that can do the same work otherwise...

---

### Post by SeijiSensei on 2010-11-29
There's always the option of a cron job to run apt-get every night.

---

### Post by CharlesA on 2010-11-29
It's not a security issue in that there is nothing to exploit that would compromise the machine.

What SeijiSensei said. Cronjobs are great. :)

---

