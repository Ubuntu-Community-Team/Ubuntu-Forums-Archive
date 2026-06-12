---
title: "which package supplies /usr/share/calendar/* and are there more 'calendar' files?"
date: 2007-01-07
forum: The Cafe
---

### Post by ice60 on 2007-01-07
hi, when i use ubuntu i have this bash_alias -
```
alias today='grep -h -d skip `date +%m/%d` /usr/share/calendar/*'
```
which runs this -
```
grep -h -d skip `date +%m/%d` /usr/share/calendar/*
```
i want to be able to use it in other distros and if possible add even more files.

so, can someone tell me where i can get those files from, or which package they come in and if there are any extra files which can be downloaded? i was thinking of something like the extra star trek files you can get with fortune :cool:  :D  thanks, i hope someone can help :)

---

### Post by UbuWu on 2007-01-07
package: bsdmainutils

---

### Post by ice60 on 2007-01-07
> **UbuWu said:**
> package: bsdmainutils

great, thanks UbuWu :cool:

---

### Post by cusco on 2008-03-29
and you can just use the command "calendar"

---

### Post by 23meg on 2008-03-30
You can find out which package supplies a certain file with ```
dpkg -S filename
``` or ```
apt-file search filename
``` apt-file will search the whole archive whereas dpkg -S will search locally installed packages.

And please keep support threads to support forums.

---

### Post by ice60 on 2008-03-30
> **23meg said:**
> You can find out which package supplies a certain file with ```
dpkg -S filename
``` or ```
apt-file search filename
``` apt-file will search the whole archive whereas dpkg -S will search locally installed packages.

And please keep support threads to support forums.

thanks, 23meg. i don't think i was running ubuntu at the time, i just had the alias, it wasn't ubuntu support.

---

