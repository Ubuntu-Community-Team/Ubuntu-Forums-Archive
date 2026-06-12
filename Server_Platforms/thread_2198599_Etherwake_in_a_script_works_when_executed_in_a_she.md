---
title: "Etherwake in a script works when executed in a shell but no in in cron"
date: 2014-01-09
forum: Server Platforms
---

### Post by aconsuegra2 on 2014-01-09
I am configuring a backup in ubuntu server.
It consists in a second server, powered by POE (etherwake command) in the backup script.
When i execute the script, as root in a ssh shell session, the backup server is powered on as expected, but if i program a job in crontab, the etherwake commnad does nor power up backup server.
Everithing in the backup script works just as expected, except the etherwake command.
If i execute the etherwake command in another ssh session, the backup ends ok.
The crontab job is added in the root account (executed as root)

Relevant parts of script home-sync.sh
```

#!/bin/bash
#
TYPE="sync"
HOST="prodsvr"
LOGFILE="/home/copias/bck$TYPE`date +%y%m%d`.log"
SOURCE="/home/"
DESTDIR="/home/copias/home"
DESTHOST="bcksvr"
DESTPH="00:10:a1:f0:01:c0"
WAIT=1
BCKBOOT=0
echo `date`: Iniciada copia a sistema de respaldo > $LOGFILE
while [ $WAIT -le 15 ]
do
        PING=$(ping -c 1 $DESTHOST 2>&1| grep "% packet" | cut -d" " -f 6 | tr -d "%")
        if [ "$PING" = 0 ]
                then
                        echo `date`: $DESTHOST está vivo >> $LOGFILE
                        WAIT=15
                        BCKBOOT=1
                else
                        echo `date`: Despertando $DESTHOST pase $WAIT >> $LOGFILE
                        etherwake $DESTPH
                        sleep 1m
        fi
        (( WAIT++ ))
done
.
.
.



```


And the contab line in root accout:
```
00 02 * * * /home/copias/home-sync.sh

```

How is it possible?

---

### Post by steeldriver on 2014-01-09
Hello and welcome to the forums

Where is the etherwake command located? it may be in *your* path, but not in cron's path. It's good practice to use absolute paths for all commands in cronjobs just to be sure.

---

### Post by CharlesA on 2014-01-09
Use the full path.

I don't use etherwake, I use wakeonlan in my script.

```
#!/bin/bash

# Path variables
ping=/bin/ping
rsync=/usr/bin/rsync
wakeonlan=/usr/bin/wakeonlan
grep=/bin/grep
ssh=/usr/bin/ssh
mail=/usr/bin/mail
date=/bin/date

# rsync/ssh variables
source=/array/.
destination=/backup/
user=root
host=loki

# Email variable
email=user@domain
longdate=$($date +%D)

# counter variables
i=1
timeout=120

# Get Date/Time backup started
startdate=$($date +%D)
starttime=$($date +%T)
start=$($date +%s)


# Check to see if host is up, and if it isn't send magic packet
if [[ -z $($ping -c 1 -W 1 $host | $grep icmp_req=1)  ]];
then
        $wakeonlan 00:23:54:47:94:4f
else
        echo "Host is already up"
fi
# Wait until $timeout to make sure host is up.
while [[ -z $($ping -c 1 -W 1 $host | $grep icmp_req=1) ]];
do
        sleep 1 && echo $i
        if [[ $i = $timeout ]]; then break
        fi
i=$((i +1))
done

if [[ $i = $timeout ]];
then
        echo "$host not up after $timeout seconds!" | $mail -s "$host not up to sync to!" $email; exit 1
else
# Wait 15 seconds to make sure ssh is running and machine is fully booted
        echo "Host is up, waiting 15 seconds to make sure ssh is running..." && sleep 15 && echo "Running rsync..." &&  $rsync --archive --itemize-changes --delete --exclude lost+found $source $user@$host:$destination

# Get Date/Time backup completed
stopdate=$($date +%D)
stoptime=$($date +%T)
end=$($date +%s)

fi
if [[ $? -ne 0 ]];
then
        echo "Rsync encountered an error!" | $mail -s "Sync with $host failed!" $email && $ssh $user@$host 'shutdown -h -P now'
else
        $ssh $user@$host 'shutdown -h -P now'
fi

# Send email of success
(echo "Backup started at:  $startdate  $starttime" && echo "Backup finished at: $stopdate  $stoptime" && echo && echo "Duration in seconds: $(($end-$start))") | $mail -s "Sync to Loki complete for $longdate" $email

```

---

### Post by aconsuegra2 on 2014-01-10
outch....Thanks to both charlesa and steeldriver. A newbie fail....
I have added at the begining:
```
GREP="$(which grep)"
PING="$(which ping)"
WAKE="$(which wakeonlan)"
#WAKE="$(which etherwake)"
SLEEP="$(which sleep)"
MAIL="$(which mail)"
SSH="$(which ssh)"
CUT="$(which cut)"
TR="$(which tr)"
MAIL="$(which mail)"
```

This make the script moore portable in other systems.

BTW, etherwake does not work in crontab, even with full path to binary. I have used wakeonlan (thx again charlesa) but i have to add -i option: "wakeonlan -i [net broadcast addr] [physical addr]"
Everithing is now working as expected.

---

