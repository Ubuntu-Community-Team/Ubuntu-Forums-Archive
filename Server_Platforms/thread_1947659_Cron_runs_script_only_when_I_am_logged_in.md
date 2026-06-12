---
title: "Cron runs script only when I am logged in"
date: 2012-03-27
forum: Server Platforms
---

### Post by FreeD01 on 2012-03-27
Hello, I run server 10.04 LTS. I have created backup script and I want to run it as a cron job. Script works fine, I have added a line into **/etc/crontab**:

**01 1    * * *   root    cd / && /home/username/script**

Problem is cron runs the script only when I am logged in. When I am logged out it does not. I got this line in /var/log/cron.log after I have set the job for testing to 8:36 and then logged out.

**Mar 27 08:36:01 ComputerName CRON[19576]: (root) CMD (cd / && /home/username/script)**

I have tried to set cron by

**sudo crontab -e**

with the same result. I think problem is in the script as it seems from the log that cron attempts to run it. Script does not have "." in its name, I use full paths and I can run it from command line with no problem. Is there something about cron jobs what I have missed? The script is:

```
#!/bin/bash
#Set a backup directories:
bdir="/backup/"
ydir="/backup/year/"
wdir="/backup/week/"
#set day of the week
date=$(date '+%u')

echo "Backup script initiated: "$(date '+%c') >>${bdir}log 2>&1
if [ "$date" -eq "1" ];
then
sudo rm ${bdir}snap*.snap >>${bdir}log 2>&1
sudo tar cvpfz ${ydir}$(date '+week%V.%b.%y').tar.gz -g ${bdir}snap$(date '+%y').snap /srv/samba >>${bdir}log 2>&1
else sudo tar cvpfz ${wdir}$(date '+%u')$(date '+%a').tar.gz -g ${bdir}snap$(date '+%y').snap /srv/samba 2>>${bdir}log 2>&1
fi
echo "Backup script has finished: "$(date '+%c') >> ${bdir}log
echo >>${bdir}log
echo "________________________________________________________________" >>${bdir}log
echo >>${bdir}log
```

Thanks for reply :-k

---

### Post by FreeD01 on 2012-03-27
Have you tried to power off, power on? **I.T. POWER!** :lolflag:

---

### Post by hawkmage on 2012-03-27
Do you have an encrypted or auto-mounted home directory?

---

### Post by CharlesA on 2012-03-27
> **hawkmage said:**
> Do you have an encrypted or auto-mounted home directory?
That would be my first guess.

Also, if you are running the script in a root crontab, you don't need to have sudo in the script.

---

