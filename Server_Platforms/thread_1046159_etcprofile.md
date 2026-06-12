---
title: "/etc/profile"
date: 2009-01-21
forum: Server Platforms
---

### Post by Zeratul021 on 2009-01-21
Hi all, earlier today i was attempting to upgrade my server with aptitude upgrade but it failed with reason: cannot find path to ldconfig, rc-update ... 4 total. I went to /etc/profile and assumed that im in wrong branch of condition determining PATH, so I edited it to look the same.
What i quite dont understand is the condition:

```
if [ "`id -u`" -eq 0 ]; then
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11"
else                                                                              
  PATH="/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games:/sbin:/usr/sbin:/usr/local/sbin"
fi
```

As you can see the second path has "sbins" added. My question is why i was turned into the else branch of the statement therefor what does the condition mean?
Thanks, with regards,
Marek

---

### Post by spiderbatdad on 2009-01-21
not really sure but what about something like:
```
if [ "`id -u`" -eq 0 ]; then
  export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/sbin:/usr/local/bin &&
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11"

```

An example from .bashrc:
export PATH=$PATH:$HOME/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$Home/bin

---

### Post by Zeratul021 on 2009-01-21
wow,thanks but sorry, i dont really get what you wanted to say with that piece of code, i just need to have that condition explained
Thanks

---

