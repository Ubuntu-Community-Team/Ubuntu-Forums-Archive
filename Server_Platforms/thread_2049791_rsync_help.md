---
title: "rsync help"
date: 2012-08-29
forum: Server Platforms
---

### Post by bakegoodz on 2012-08-29
I finally setup my offsite back for /home on my home computer, but my backup copy has been out of sync for a month. So I did a manual rsync to make sure I get it right before I set it as cron job. I left it to run overnight, but I found it this morning coping already existing files. I'm sure I got both folders right and I didn't find duplicates. I will do another manual device to device sync onsite and then try a remote rsync again. My question is: Is there a problem with my syntax? Is is set to copy just changes?
```
rsync -avH -e ssh --progress user@user.dyndns.com:/home/user /media/backup/user
```

---

### Post by SeijiSensei on 2012-08-29
Using the "-n" switch means that the files will not actually be transferred; that's the "dry-run" option for debugging purposes.

Next, if you want to make /media/backup/user be identical to the remote's /home/user, you should use /media/backup as the target destination.  Otherwise you'll find you have a folder called /media/backup/user/user on the backup host.

---

### Post by Lars Noodén on 2012-08-29
I think that the directories should have the closing slash (/) for rsync to work properly.  

```

rsync -avHn -e ssh --progress user@user.dyndns.com:/home/user_/_ /media/backup/user_/_

```

---

### Post by bakegoodz on 2012-08-29
Your right, but I removed the -n on the command I ran

I will try it with the closing slash later. I think I'll get them synced again onsite first.

---

### Post by koenn on 2012-08-29
> **Lars Noodén said:**
> I think that the directories should have the closing slash (/) for rsync to work properly.  

```

rsync -avHn -e ssh --progress user@user.dyndns.com:/home/user_/_ /media/backup/user_/_

```

IIRC trailing slashes do have meaning, especially on the source dir.so they don't *need* to be there unless the effect they have suits your needs or intend.

I usually put a trailing slash on the source dir, and not on the destination dir, because I find that the most intuitive : I think of the trailing (source dir) slash as 'short for .../*'

so
```

rsync /home/koenn/   user@server:/backups/koenn

```
reads as : contents of /home/koenn/ goes to /backups/koenn

this also handles the directory issue SeijiSensei pointed out

---

