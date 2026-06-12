---
title: "instructions executed by root"
date: 2015-01-29
forum: Security
---

### Post by Juan_Perez on 2015-01-29
Hello !

The instruction
```
sudo find / -perm -4000
```

shows me the processes executed with root privileges... except for the last lines.

[IMG]http://i.imgur.com/Za4gsGP.png[/IMG]

I am not sure how to interpret these "find" instructions. Certainly, the proc/18109 directory does not exist but why are they listed as programs ? Any help is appreciated. 

Thanks !

---

### Post by Juan_Perez on 2015-01-29
Something else, if i run

```
find / -type f -perm 0777
```

to list the files with permission 777, the same lines "find: .." are shown !

---

### Post by steeldriver on 2015-01-29
Those lines are *errors* from the [FONT=courier new]find[/FONT] command - telling you that it cannot test the files in /proc (because they already disappeared). The /proc filesystem is a "virtual"  filesystem containing information about current processes,so its contents are volatile (and you probably aren't interested in their permissions anyway)

If the lines bother you, you can either hide error output by redirecting it to the 'bitbucket' (null device)

```

find / -type f -perm 0777 2>/dev/null

```

or (more elegantly), tell find to skip ('prune') the /proc filesystem

```

find / -path /proc -prune -o -type f -perm 0777 -print

```

or to skip other virtual filesystems /sys and /run as well

```

find / \( -path /proc -o -path /run -o -path /sys \) -prune -o -type f -perm 0777 -print

```

---

### Post by Juan_Perez on 2015-01-30
Thanks for the answer !
Just one more question, is it possible to determine who executed these *find* instructions ? 
Is it safe to say it was NOT a user?

---

### Post by steeldriver on 2015-01-30
No, there is nothing to stop any user from executing find on the / dir - there will just be more errors (because some system directories will be inaccessible to non-root users)

You *might* be able to see if root (or someone assuming root, via sudo) executed them by looking in the /var/log/auth.log

---

### Post by Juan_Perez on 2015-01-30
Sorry, just one more question .
Why are these instructions being shown ? 
Are they part of a program ?
Why aren't other instructions executed by root being shown ?

---

### Post by steeldriver on 2015-01-30
**Where** are they being shown? please give us some context - what are you doing when you see them?

---

### Post by SeijiSensei on 2015-01-30
The numerical directories in /proc are created by tasks as they are run.  Many tasks run for only a few seconds and terminate.  The directory existed when the find program began, but by the time it actually got to that directory, the process had already ended.

There is nothing of interest in /proc for most users unless you're looking for particular pieces of information like the lists in /proc/modules or /proc/interrupts.

---

### Post by Juan_Perez on 2015-02-01
They are listed when I look for programs that can be executed by root. 
I just thougtht it was strange because the rest of the list were commands like mount and ping. 

Thanks for all the explanations !

---

