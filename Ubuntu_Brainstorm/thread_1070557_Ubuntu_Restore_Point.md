---
title: "Ubuntu Restore Point"
date: 2009-02-15
forum: Ubuntu Brainstorm
---

### Post by seicean on 2009-02-15
I'm looking for a software/service that can make a restore point in Ubuntu. I think this is not that much of a fuss, but is the Ubuntu 9.04 team considering this option ?

Maybe I'm not the only one here that makes LOTS of mistakes in the settings/conf files and wakes up that he has to run a fresh install afterwards :)

Any ideas ?

Thanks,
Roumanian Ubuntu User

---

### Post by lensman3 on 2009-02-15
This is a very windows point of view.  Linux/Unix user the backup/restore model.  I personally use the program star (super tar) and do dumplevels.  

I would suggest a system call Plan9.  It keeps a current snap shot of all your drives and you can restore from any date.

---

### Post by WatchingThePain on 2009-02-15
Hi,

I just use simple sbackup tool from synaptic package manager. Otherwise I might use the 'tar' command. You get a lot of control over what's backed up, how, when and where to. There are also different types of backups like full backup or just backup changes to files. Cron is a bit like windows task scheduler and can be used to schedule backups.
Windows restore harbours viruses sometimes.

---

### Post by lensman3 on 2009-02-15
I recommended "Plan 9". I meant to say "backupfs" which is modeled after Plan 9's backup system.  Sorry.

---

### Post by jpkotta on 2009-02-15
The next time I reinstall, I'm going to put all of the system config files that I edit by hand under revision control (I prefer Mercurial).  I already do this for a large portion of my user's config files, and it works pretty well.  The disadvantage is that it takes discipline, the advantage is that it is more flexible.  Obviously not really a replacement for backups, but a decent solution to OP's problem.

---

### Post by seicean on 2009-02-16
@lensman3: I know this is Windows point of view, but considering the large migration from Windows to Ubuntu, You can say that this is much more than expected. The new user will always make "connections" with Windoze.

Thanks guys. I will obiously take a look and come back with a result

---

