---
title: "apt-log"
date: 2008-12-03
forum: The Cafe
---

### Post by mavior on 2008-12-03
This started as my need and then I have decided to release it.
I hope that will be useful for somebody, you have all here [http://mavior.eu/apt-log]("http://mavior.eu/apt-log")  
Feedbacks are much welcomed.

---

### Post by binbash on 2008-12-03
I was bored messing with .bash_history.I am going to try it soon

EDIT : 

It just gives an error : 

Can't open apt configuration file "/etc/apt/apt.conf" : No such file or directory.

Where is the config file?

---

### Post by Kingsley on 2008-12-03
```
less /var/log/dpkg.log
```

---

### Post by mavior on 2008-12-03
> **binbash said:**
> 
EDIT : 

It just gives an error : 

Can't open apt configuration file "/etc/apt/apt.conf" : No such file or directory.

Where is the config file?

Sorry, this is due to an erroneous assumption: I have just corrected and updated the archive.You can download it from the same place.

---

### Post by mavior on 2008-12-05
> **Kingsley said:**
> ```
less /var/log/dpkg.log
```

This has nothing to do with the purpose of apt-log itself.Or better: apt-log can also dump (with --dump) all the informations from the logs.
But again: apt-log is not meant as dump tool.It's a log analyzer and report tool.

---

