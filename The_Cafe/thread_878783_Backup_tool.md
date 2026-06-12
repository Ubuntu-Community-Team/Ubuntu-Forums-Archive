---
title: "Backup tool"
date: 2008-08-03
forum: The Cafe
---

### Post by clinux on 2008-08-03
After managing all my problems in ubuntu and feeling very lucky, I started feeling that my computer is very fragile and I don't want to lose all my configuration files.
So I'm wondering if anyone knows a good massive backup tool that will detect and copy all my important config files.

thanks

ps: if possible i would like it to detect config files from programs as well

---

### Post by 50words on 2008-08-03
You just need to copy your /home directory. Search the forums for rsync tutorials. Once you get it working the way you like, install a cron tool to run your rsync backup on a schedule.

---

### Post by Mateo on 2008-08-03
I also have backup needs.  However, i don't want mine going on a schedule because A) I don't have my computer on all the time so it might not be on during the scheduled time B) I probably want to backup to a thumb drive and those aren't always in either.  So I need a backup solution that runs on my schedule.

---

### Post by Polygon on 2008-08-03
there is a program in the repos called pybackpack (gui) so if you dont want to mess with the command line, that will work

but i personally use rdiff-backup (cli), it makes incremental backups and you can choose the date you want to restore if anything goes wrong.

---

### Post by armageddon08 on 2008-08-04
You can use 'Remastersys'---[Remastersys home]("http://www.remastersys.klikit-linux.com/")

---

### Post by beercz on 2008-08-04
I like [rsnapshot]("http://rsnapshot.org")

---

### Post by LaRoza on 2008-08-04
> **clinux said:**
> After managing all my problems in ubuntu and feeling very lucky, I started feeling that my computer is very fragile and I don't want to lose all my configuration files.
So I'm wondering if anyone knows a good massive backup tool that will detect and copy all my important config files.

thanks

ps: if possible i would like it to detect config files from programs as well

Which config files? For all user settings, it will be in your home.

---

