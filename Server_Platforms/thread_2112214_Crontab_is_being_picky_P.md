---
title: "Crontab is being picky :P"
date: 2013-02-04
forum: Server Platforms
---

### Post by Valpskott on 2013-02-04
So, I've made 3 entries to the crontab of my user.

```

0 6 * * * /home/johan/yt-stats/day.sh
10 6 * * 1 /home/johan/yt-stats/week.sh
20 6 * * * /home/johan/yt-stats/update.sh

```

Running "ls -lu /home/johan/yt-stats/*.sh" gives me this:
```

-rwxrwxr-x 1 johan johan 849 feb  4 06:00 day.sh
-rwxrwxr-x 1 johan johan 129 feb  3 09:04 update.sh
-rwxrwxr-x 1 johan johan 872 feb  4 06:10 week.sh

```

It tells me that update.sh was never executed(read) at that time (6:20 in the morning), but the other two scripts where (6:00 and 6:10 respectivly as should be on a monday morning).

Any insight or help is greatly apprechiated.

---

### Post by SeijiSensei on 2013-02-04
Make sure any commands in the scripts use their full paths.

Do the scripts start with "#!/bin/bash" as the first line?  If not, they might be running with the more limited shell Ubuntu uses called "dash".  In general, for a cron script I use something like:

```

#!/bin/bash

/path/to/some/command something


```

---

### Post by Valpskott on 2013-02-04
Thank you for your response.

The entire script looks like this.

> #!/bin/bash

cp -fr /home/johan/yt-stats/vecka.html /var/www/vecka.html
cp -fr /home/johan/yt-stats/dag.html /var/www/dag.html


But even if "#!/bin/bash" was missing, wouldn't the file be marked as accessed(read) at 6:20 anyways, even if it wasn't able to execute the content of the script properly?

---

### Post by SeijiSensei on 2013-02-04
Does the script run as a user with permissions to write to /var/www?  What do you see in /var/log/syslog at the time the script should be running?

---

### Post by Valpskott on 2013-02-05
Ehm, yeah... I was under the illusion that everything executed through crontab was done so with sudo privileges (as long as the user had sudo-privileges).

I now set johan:root as the owner of www and all files below it, and the crontab ran fine. I also noticed that it doesn't always show up in "ls -lu" if a file has been accessed, or maybe it shouldn't?

Thank you for helping me sort this problem! :)

---

### Post by SeijiSensei on 2013-02-05
Entries in /etc/crontab or crontabs created by using "sudo crontab -e"  and stored in /var/spool/cron/root run with root privileges. If you use "crontab -e" as an ordinary user, the crontab will be stored as /var/spool/cron/username and run with that user's privileges.

In /etc/crontab you need to specify the user explicitly like this:
```
1 1 * * * root /bin/bash /path/to/script
```
You can force a command in /etc/crontab to run with another user's privileges by replacing "root" with that username.

---

