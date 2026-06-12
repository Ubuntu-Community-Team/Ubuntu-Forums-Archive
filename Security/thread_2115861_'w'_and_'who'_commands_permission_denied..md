---
title: "'w' and 'who' commands: permission denied."
date: 2013-02-14
forum: Security
---

### Post by kleenex on 2013-02-14
Hi, Could anybody tell me if [COLOR=Green]w[/COLOR] and [COLOR=Green]who[/COLOR] commands can't be running by a normal user due to permission denied? In this case, it looks in this way:

```
[COLOR=Red][~][/COLOR][COLOR=Blue]$[/COLOR] [COLOR=Green]w[/COLOR]
bash: /usr/bin/w: Permission denied

[COLOR=Red][~][/COLOR][COLOR=Blue]$[/COLOR] [COLOR=Green]who[/COLOR]
bash: /usr/bin/who: Permission denied
``` So, it is normal on a default Xubuntu 12.04 installation? I'm sorry for asking, but for now I have no possibility to check/verify it and it's pretty important. 

Thanks.

---

### Post by schragge on 2013-02-14
Look at the file permissions:
```

ls -l /var/run/utmp /var/log/*tmp

```

---

### Post by kleenex on 2013-02-14
Hi **schragge**. Sorry for asking, but what does that have to do with my question? Okay: [COLOR=Green]/var/log/*tmp: No such file or directory[/COLOR] and [COLOR=Green]/var/run/utmp[/COLOR] is owned by root and utmp.

---

### Post by matt_symes on 2013-02-14
Hi
 
```
/var/run/utmp is owned by root 
```
 
That may be the problem.
 
Can you post the output of 
 
ls -l /var/run/utmp
 
to check the read permissions.
 
Kind regards

---

### Post by howefield on 2013-02-14
They can be run by a normal user, that is, without elevated priveleges.

---

### Post by bantuvez on 2013-02-14
I would be more interested in the permissions of the files mentioned in the OP. So why not post the results of

```

ls -l /usr/bin/w 
```?

And because at me it is a link to /etc/alternatives/w which is a link to /usr/bin/w.procps :

```

ls -l /etc/alternatives/w /usr/bin/w.procps

```

---

### Post by kleenex on 2013-02-14
Hi, I will do this everything, which You have asked for. But for now I would like to know if e.g. turn off the SUID bit (with [COLOR=Blue]chmod -s[/COLOR] command) from those files, may cause these Permission denied problems? But generally: it is normal and default result for the average user who's trying to run [COLOR=Green]w[/COLOR] and [COLOR=Green]who[/COLOR] commands?

**matt_symes**; [COLOR=Green]/var/run/utmp[/COLOR] file -rw-rw-r--

---

### Post by schragge on 2013-02-15
> **bantuvez said:**
> I would be more interested in the permissions of the files mentioned in the OP.Although I doubt you'll find anything unusual there, I think
```
namei -l /usr/bin/w{,ho}
``` is more informative in this regard.

---

