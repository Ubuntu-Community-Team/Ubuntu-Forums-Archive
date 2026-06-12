---
title: "Apparmor log all changed / created files"
date: 2012-11-23
forum: Security
---

### Post by Esokra on 2012-11-23
Hello, 

As part of a project, I need to log the filenames (including path) of files that have been changed or created by an enforced process (e.g. firefox) in special directories (I tried Downloads). Although I set to profile to audit, it only shows me the directory where changes where made (in my case the Downlaods directory). For me it is especially important to figure out, whether a new file has been created or not (this information I would like to store in a seperate log, if possible). Is apparmor capable of doing that?
If not, has anybody an idea how to achieve this, together with apparmor and a special program (e.g. inotify)? In this case it would be important to know, how to make apparmor starting a special script or program for at the startup of an enforced application. 

Thank you very much in advance!

---

### Post by Hungry Man on 2012-11-23
Apparmor only logs violations, it doesn't log anything with an 'allow' rule AFAIK. There may be some other log, or certainly a program.

---

### Post by Esokra on 2012-11-23
Apparmor does also log other things than violations, but as I experienced only the type of action (open etc.) and the folder, which is affected (at least in audit mode). Is there no way to achieve something like this? (I thought because it is path based this is possible).

---

