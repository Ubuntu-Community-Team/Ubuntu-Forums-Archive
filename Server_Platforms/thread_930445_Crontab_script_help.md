---
title: "Crontab script help"
date: 2008-09-26
forum: Server Platforms
---

### Post by stonneway on 2008-09-26
Hi chaps,

Can anyone help me with creating a script that will output the crontab entries for all the users on a Ubuntu box ? 

We had a user on one of our ubuntu servers who got all cocky and decided to create lots of crontab entries for various things and as a result brought the server to a crippling halt. We now want to just make sure non of his colleagues are doing the same thing and thought it was best practice to go over them all.

S.

---

### Post by bluefrog on 2008-09-26
```
for i in $(awk 'BEGIN{FS=":"} {if ($3 >= 1000) print $1}' /etc/passwd ); do echo "cron for $i" && echo $i | sudo crontab -u $i -l; done &> file
```

---

### Post by willca on 2008-09-26
You might want to consider denying crontab access those who abuse it.

/etc/cron.allow
/etc/cron.deny

---

