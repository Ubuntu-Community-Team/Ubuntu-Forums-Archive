---
title: "Windows XP with VBOX - desktop.u1conflict"
date: 2013-05-06
forum: Virtualisation
---

### Post by ray45c on 2013-05-06
My Ubuntu 12.04 recently did a software upgrade and afterwards I got an icon on my desktop that reads: Windows XP.desktop.u1conflict
If I try to launch Windows XP in VBOX a window pops up that says "Failed to open a session for the virtual machine."  I can click on OK or Copy.  I don't know how to get my VBOX session working and was hoping someone could guide me.  I'm a novice at both Ubuntu and VBOX.
Thanks in advance!!

---

### Post by deadflowr on 2013-05-06
The u1.conflict means you have the file in your Ubuntuone account, but that this one is different somehow than the normal one, which is why it says conflict. Usually because the two files share the same name.

Not really helpful as to the main problem, but I felt I should point that out.

---

### Post by ray45c on 2013-05-08
Thank you for the input Deadflowr.  Don't think it will help because I don't know enought about Ubuntu to figure the wrong or right file but I appreciate the help.

---

### Post by wildmanne39 on 2013-05-08
*Thread moved to **Virtualisation**.*

---

### Post by taidoka on 2013-05-12
@ray45c
Did you check if the path to your vm is correct?
Did the error message look something like that?

[ATTACH=CONFIG]242520[/ATTACH]

---

### Post by taidoka on 2013-05-12
@ray45c
Right-click that icon > properties > location: ???
[B]
Check if ubuntuone service is running[/B]
In a terminal paste:
```
pgrep ubuntuone
```
If it's not running no value will be returned.
To start Ubuntu One type in a terminal:
```
ubuntuone-installer
```

---

