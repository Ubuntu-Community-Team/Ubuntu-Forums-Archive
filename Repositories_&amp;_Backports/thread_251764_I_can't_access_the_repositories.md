---
title: "I can't access the repositories"
date: 2006-09-05
forum: Repositories &amp; Backports
---

### Post by shousonhill on 2006-09-05
I can't access the repositories.  Anyone else having this problem?

I have reloaded my /etc/apt/sources.list w/ Ubuntu_demon's sources.list template but it still doesn't work.

---

### Post by aysiu on 2006-09-05
Can you post the output of this command? ```
sudo aptitude update
```

---

### Post by shousonhill on 2006-09-06
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.54 80]

---

### Post by aysiu on 2006-09-06
Maybe [this](http://www.ubuntuforums.org/showpost.php?p=1139641&postcount=41) might help.

---

### Post by shousonhill on 2006-09-06
That worked!  Thanks for the help!

---

