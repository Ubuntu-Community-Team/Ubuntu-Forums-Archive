---
title: "Filesystem Audit... how to monitor what files are read in a given directory?"
date: 2008-06-26
forum: Security
---

### Post by niiiick on 2008-06-26
Hi guys,

so i want to run some kind of script or app that will log all read functions of all files in a given directory.

i've come across inotify and auditd (i think that's what it was called, but something like that) but as far as i can tell inotify doesn't log file reads, and auditd can't monitor whole directories for file reads.

can anyone help?

thanks,
nick

---

### Post by brian_p on 2008-06-26
> **niiiick said:**
> Hi guys,

so i want to run some kind of script or app that will log all read functions of all files in a given directory.

i've come across inotify and auditd (i think that's what it was called, but something like that) but as far as i can tell inotify doesn't log file reads, and auditd can't monitor whole directories for file reads.

Has tripwire anything to offer you?

---

### Post by cdenley on 2008-06-27
Isn't this what you want?
```

inotifywait -e OPEN -m /path/to/mydir>/path/to/my.log

```

Or did you want it to be recursive?
```

inotifywait -r -e OPEN -m /path/to/mydir>/path/to/my.log

```

---

### Post by niiiick on 2008-06-27
tried tripwire... was a bit overkill...

the inotify thing worked wonders.  thanks a million.

---

