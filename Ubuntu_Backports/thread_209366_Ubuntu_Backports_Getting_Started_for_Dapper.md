---
title: "Ubuntu Backports Getting Started for Dapper"
date: 2006-07-05
forum: Ubuntu Backports
---

### Post by RobNyc on 2006-07-05
How do I get started using backports for dapper if possible?

---

### Post by mlind on 2006-07-05
[QUOTE=RobNyc]How do I get started using backports for dapper if possible?[/QUOTE]

You just have to enable backports repositories. Put this on /etc/apt/sources.list
```

deb http://archive.ubuntu.com/ubuntu/ **dapper-backports** main restricted universe multiverse

```

---

### Post by RobNyc on 2006-07-05
Thanks

I didn't notice Automatix had done it for me already

---

### Post by FredB on 2006-07-06
Now, let's wait for backports :)

Which one to be the first ? OpenOffice.org ? Rythmbox ?

---

### Post by Gustav on 2006-07-06
I'm trying to decide if I should wait for the backport of rhythmbox or if I should find a .deb and install it right now.

The time it takes to make the decision (probably a week or so :)) is probably so long that the backport will arrive before I've decided. :)

---

### Post by FredB on 2006-07-06
:lol:

Indeed. I think backports is a safer and simpler way.

---

