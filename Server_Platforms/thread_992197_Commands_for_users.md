---
title: "Commands for users?"
date: 2008-11-24
forum: Server Platforms
---

### Post by skyggen on 2008-11-24
Hey! 

I have setup an ubuntu server with open-ssh for users.Made everything look good by getting my help from here and google. Now i want to know how i can make so that when users type "vhosts" when logged in to the shell, they get a list of the current vhosts i have added to the list, simply printing out text. I also want to make stuff like that for info and help. example: "psybnc-help" and so on.

How do i go about this, bash scripts? if so, where should these scripts be located so that every users can type, "vhosts" ?

---

### Post by cdenley on 2008-11-24
> **skyggen said:**
> Hey! 

I have setup an ubuntu server with open-ssh for users.Made everything look good by getting my help from here and google. Now i want to know how i can make so that when users type "vhosts" when logged in to the shell, they get a list of the current vhosts i have added to the list, simply printing out text. I also want to make stuff like that for info and help. example: "psybnc-help" and so on.

How do i go about this, bash scripts? if so, where should these scripts be located so that every users can type, "vhosts" ?

Create this file:
/usr/bin/vhosts
```

#!/bin/sh
ls -1 /etc/apache2/sites-enabled

```
then make it executable
```

sudo chmod 755 /usr/bin/vhosts

```

When you run a command without a path, it looks in the paths stored in the PATH environment variable.
```

echo $PATH

```

---

### Post by CrucifiedEgo on 2008-11-24
Technically, /usr/local/bin is where your custom scripts should go, according to the [FHS]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").  cdenley's script looks good as long as you're following the debian way of handling vhosts.

---

### Post by skyggen on 2008-11-24
That answers my question about the scripts and it's location.
Thank you very much ^^

---

