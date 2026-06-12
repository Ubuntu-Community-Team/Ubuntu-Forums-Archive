---
title: "Cron doesn't echo to file"
date: 2011-03-27
forum: Server Platforms
---

### Post by fela on 2011-03-27
I have a script, echoSmart.sh:

```
#!/bin/bash
smartctl -a /dev/sda > /smartlogs/sda-$(date).txt
smartctl -a /dev/sdb > /smartlogs/sdb-$(date).txt
exit 0

```

This script, when run by hand (sh echoSmart.sh) runs fine and outputs the SMART data to the log.

However, when run as a cronjob (in root's cron), it produces files but they're both empty!

What can the matter be?

---

### Post by rubylaser on 2011-03-27
You should use full paths in scripts to be used by cron. I would tweak your script like this...

```

#!/bin/bash
TODAY=`date +%m%d%y`

/usr/sbin/smartct -a /dev/sda > /smartlogs/sda-"$TODAY".txt
/usr/sbin/smartct -a /dev/sdb > /smartlogs/sdb-"$TODAY".txt
exit 0

```

---

### Post by fela on 2011-03-27
> **rubylaser said:**
> You should use full paths in scripts to be used by cron. I would tweak your script like this...

```

#!/bin/bash
TODAY=`date +%m%d%y`

/usr/sbin/smartctl -a /dev/sda > /smartlogs/sda-"$TODAY".txt
/usr/sbin/smartctl -a /dev/sdb > /smartlogs/sdb-"$TODAY".txt
exit 0

```

Thanks, that worked perfectly! :guitar:

Btw, I did actually have the date variable but thought it was irrelevant to mention that in the OP :)

---

### Post by rubylaser on 2011-03-27
No problem, glad it's working :)

---

