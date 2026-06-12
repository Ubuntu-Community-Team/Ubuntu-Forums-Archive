---
title: "Back up software"
date: 2006-03-13
forum: Server Platforms
---

### Post by stabface on 2006-03-13
I work at a small office about 15 machines all running winXP, and me running Ubuntu. I built a server using ubuntu server install out of a old pent III, it works well enough for sharing files. But my boss wants something that can auto back up certain drives on machines in the office. like this program. [http://www.tgrmn.com/](http://www.tgrmn.com/)

---

### Post by Koybe on 2006-03-13
On which support do you plan to backup?

If it's disk to disk, just have a look at Backuppc, it's a great peace of software. If you need external backup, look at small software like backup2l or much intersting (and complicated ones) like bacula or amanda.

---

### Post by stabface on 2006-03-13
i am looking for disk to disk, from windows XP workstations backed up on the Ubuntu sambs server back up folders

---

### Post by derelict on 2006-03-13
If the server can access the client shares it seems that you can simply use [cron]("http://www.scrounge.org/linux/cron.html") to schedule an execution of [tar]("http://www.google.pt/search?hs=QEc&hl=pt-PT&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=tar+backup&btnG=Pesquisar&meta=") to backup the desired shares.

---

### Post by Koybe on 2006-03-14
[QUOTE=derelict]If the server can access the client shares it seems that you can simply use [cron]("http://www.scrounge.org/linux/cron.html") to schedule an execution of [tar]("http://www.google.pt/search?hs=QEc&hl=pt-PT&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=tar+backup&btnG=Pesquisar&meta=") to backup the desired shares.[/QUOTE]

That's BackupPC's job with a nice web interface. Go for it :)

---

