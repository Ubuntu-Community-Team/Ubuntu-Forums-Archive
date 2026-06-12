---
title: "Using a feisty repo on gutsy?"
date: 2007-09-29
forum: Repositories &amp; Backports
---

### Post by synd7 on 2007-09-29
So i'm on gutsy and i want to use the medibuntu repos but theres no gutsy repo. Will it hurt anything if i use a feisty repo in gusty (obviously i wont be downgrading things)

Probably a non-event but i thought i'd best make sure :)

---

### Post by Lord Illidan on 2007-09-29
Is there anything you specifically want to install from the repos?

---

### Post by synd7 on 2007-09-29
libdvdcss specifically.

Theres a few other feisty repos that i'd like to use too so i though i should at least check before going ahead

---

### Post by Lord Illidan on 2007-09-29
You can install libvdcss on gutsy very easily..Just install libdvdread and then run this script with sudo :

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by synd7 on 2007-09-29
What about for other repos? Is it in general a bad idea to mix repo versions?

---

### Post by ptn107 on 2007-09-29
My medibuntu repos link is 'deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free', and yes it does exist for gutsy.

---

### Post by synd7 on 2007-09-29
Oh, i didn't know that was there :eek:
I had a look using the community docs method and it gave me some permission denied errors.

Thanks for that :)

---

