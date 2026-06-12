---
title: "CRON Problems"
date: 2010-07-18
forum: Server Platforms
---

### Post by AntiBodies on 2010-07-18
Ok I would search the forums for examples but Ive already tried to simplify everything and am using many examples. I cant seem to get cron to run my backup script. even a test script.. here is my test script:

```
echo blingdog is currently $USER at - $(date '+%A - %d %B %Y at %H%M') >>/home/sysadmin/blingdog.txt
echo >>/home/sysadmin/blingdog.txt

exit

```

just some random stuff that will give the user and the date and output to a file right..

ok I can run this script according the tutorial here: [https://help.ubuntu.com/8.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/8.04/serverguide/C/backup-shellscripts.html)

that is running ```
bash ~/test.sh
``` or ```
sudo bash ~/test,sh
```.. I want the backup script to run as root naturally so am interested that root can run fine. now to the CRON part.

I am using ```
sudo crontab -e
``` to edit the root crontab and have added the following:

```
PATH=/usr/sbin:/usr/bin:/sbin:/bin

# m h  dom mon dow   command
30 21   * * *   bash /home/sysadmin/test.sh
```

I am adjusting the times to run at a certain point but NOTHING HAPPENS!

What am I doing wrong? I am baffled. ive adjusted most things a thousand times and am still getting nowhere. I am reading the output of the file and the output of syslog to no avail..

---

### Post by AntiBodies on 2010-07-18
ok nevermind have fixed it

omg cron service wasnt even started for some weird reason.

starts fine on restart and working fine..

---

### Post by brettg on 2010-07-18
Please mark the thread as "Solved"

---

