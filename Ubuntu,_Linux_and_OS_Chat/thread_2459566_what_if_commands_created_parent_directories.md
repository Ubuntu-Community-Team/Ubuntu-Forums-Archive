---
title: "what if commands created parent directories"
date: 2021-03-21
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2021-03-21
what if it had been traditional for commands that would be trying to place a file object somewhere (such as the "mv" command) would, by default, create all the needed parent directories automatically just like mkdir does with the -p option?  what kinds of problems could this cause?

---

### Post by TheFu on 2021-03-23
You mean like 
[LIST]
[*]mkdir -p
[*]rsync
[/LIST]
do?  There's nothing to prevent anyone from creating a "smart-mv" command as a script.

---

### Post by Skaperen on 2021-03-23
i already mentioned *mkdir* with the *-p* option.  *rsync* does not create parent directories when you specify a target path that does not have a parent.
```

lt2a/forums /home/forums 6> ls -dl foo
/bin/ls: cannot access 'foo': No such file or directory
lt2a/forums /home/forums 7> ls -dl xv
drwxr-xr-x 3 forums forums 4096 Jun 11  2020 xv
lt2a/forums /home/forums 8> rsync -a xv foo/bar
rsync: mkdir "/home/forums/foo/bar" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(675) [Receiver=3.1.2]
lt2a/forums /home/forums 9> 

```

yes, i have created such a script.  if the target exists and is not a directory, it does not replace it.  and i also made a "smart-ln", too.  in Python3, of course.

---

### Post by TheFu on 2021-03-23
Ah, I've never seen rsync used like that.  

all I can see happening with that capability is a bunch of misspelled directories being created, unintentionally and people losing files even more than they do already.

Imagine if this got implemented in a gui - ouch.

[https://stackoverflow.com/questions/18491548/rsync-create-all-missing-parent-directories](https://stackoverflow.com/questions/18491548/rsync-create-all-missing-parent-directories) ha a few options. Looks like **cp --parents** does it with a few restrictions on use. None are elegant to me for rsync.

---

