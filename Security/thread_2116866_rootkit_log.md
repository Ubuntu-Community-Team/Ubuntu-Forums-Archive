---
title: "rootkit log"
date: 2013-02-17
forum: Security
---

### Post by alfirdaous on 2013-02-17
Hello there,

While doing a scan in my server, I've got this result:

```

[06:05:56] System checks summary
[06:05:56] =====================
[06:05:56]
[06:05:56] File properties checks...
[06:05:56] Files checked: 131
[06:05:56] Suspect files: 1
[06:05:57]
[06:05:57] Rootkit checks...
[06:05:57] Rootkits checked : 245
[06:05:57] Possible rootkits: 0
[06:05:57]
[06:05:57] Applications checks...
[06:05:57] All checks skipped
[06:05:57]
[06:05:57] The system checks took: 5 minutes and 51 seconds
[06:05:57]
[06:05:57] Info: End date is Sun Feb 17 06:05:57 CET 2013


```

warning items:

```

/usr/bin/unhide.rb                                       [ Warning ]
Checking loaded kernel modules                           [ Warning ]
Checking /dev for suspicious file types                  [ Warning ]
Checking for hidden files and directories                [ Warning ]

```

is that dangerous for the website??

Thx in advance

---

### Post by unspawn on 2013-02-17
Check your rkhunter.log for details then read the README and the FAQ Rootkit Hunter comes with. In short: *know what you run*.

---

### Post by alfirdaous on 2013-02-17
thx [unspawn]("http://ubuntuforums.org/member.php?u=891049")

---

