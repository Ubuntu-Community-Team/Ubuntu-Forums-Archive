---
title: "Irc Server on debian"
date: 2008-02-08
forum: Server Platforms
---

### Post by netpumber on 2008-02-08
First of all Hi!! :D I set up debian in an old pc. And i want to install the unreal irc server. i download it and run 
```
./Config
``` in terminal.
I follow the questions and in the end it gives me this error
```
checking whether build environment is sane... configure: error: newly created file is older than distributed files!
Check your system clock

```

I cant understand what is it about ? :confused::confused: does anyone know what goes rong?Thanx  ;) :D

---

### Post by faulkes on 2008-02-08
It appears that your system clock is not set properly.

```

date

```

If the output of that command does not correspond to the actual date/time then that is what the problem is.

You may have to set the date/time in your systems bios and you may want to install the ntpd package to keep the time sync'd.

Faulkes

---

