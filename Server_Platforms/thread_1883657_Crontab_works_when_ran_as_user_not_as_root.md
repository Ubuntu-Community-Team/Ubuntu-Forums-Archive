---
title: "Crontab works when ran as user not as root"
date: 2011-11-19
forum: Server Platforms
---

### Post by McBraid on 2011-11-19
Hi all,

I've got a server running Ubuntu Server 11.10.

I've made a bash script and initially ran it automatically using a crontab as one of my regular users. It worked as intended. I started incoperating a command into the bash script that requires root acess. The script works perfectly when ran manually using

```
sudo scriptname
```

However if I configure the exact same crontab for the root user as for the regular one, moving the exact same line, using:
```
sudo crontab -e
``` instead of 
```
crontab -e
```... nothing happenes.

Any Ideas on why it won't work?

---

### Post by papibe on 2011-11-19
Hi McBraid.

crontab is a very limited environment. Usually, you need to put full paths to any command in order to work.

Could you post your crontab script?

Regards.

---

### Post by McBraid on 2011-11-20
I'm currently running this as a normal user:
```
00 8-23/3 * * * /usr/bin/statustweet
```

Nothing happenes if i use the same line for the root crontab. So I also tried to add the line:
```
PATH=/usr/sbin:/usr/bin:/sbin:/bin
``` as descibed here: [https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto") without any sucess.


The script posts status updates and random quotes and statements (if there is no change in status) on Twitter: [http://twitter.com/fra55e]("http://twitter.com/fra55e") And it would be reall nice to icoperate some sudo commands intu the status tweet.

EDIT: I've now done some further testing according to the CronHowto:
- I made sure that there is a newline after the crontab
- I also checked /var/log/syslog which seems to be all right:
```
Nov 20 10:03:01 FRAsse CRON[17066]: (root) CMD (/usr/bin/statustweet)
Nov 20 10:04:01 FRAsse CRON[17075]: (root) CMD (/usr/bin/statustweet)
Nov 20 10:05:01 FRAsse CRON[17084]: (root) CMD (/usr/bin/statustweet)

```
- Finally I added a log file which show no errors at all by editing the crontab thru "sudo crontab -e" to be:```
PATH=/usr/sbin:/usr/bin:/sbin:/bin
* * * * * /usr/bin/statustweet >> /var/log/statustweet 2>&1

```


The bash script that i run is (not very tidy but I'm still learning):
```
#!/bin/bash

TEMP="$(sensors)"
UPTIME="$(uptime)"
SPACE="$(df)"
BACKUP="$(ls -l /home/mattias/)"
#BANNED="$(fail2ban-client status ssh | grep "Total banned" | cut -f 2)"
TWEET="Uptime ${UPTIME:13:7}, last backup: ${BACKUP:46:10}, CPU temp: ${TEMP:115:2} deg, ${SPACE:132:3}GB free."
#TWEET="Uptime ${UPTIME:13:7}, last backup: ${BACKUP:46:10}, CPU temp: ${TEMP:113:4} deg, ${SPACE:132:3}GB free, blocked ssh attempts: ${BANNED}."

RESULT="$(twidge update "$TWEET" 2>&1)"
ERROR="twidge: user error (Bad response: 403)"

if [ "$RESULT" == "$ERROR" ]
   then
        NQUOTES=$(cat '/home/XXXXX/quotes' | wc -l)
        VAL=$((RANDOM%$NQUOTES+1))p
        CITAT=$(sed -n $VAL '/home/XXXXX/quotes')
        twidge update "$CITAT"
fi

```
I'm quite baffled here.. :(

---

### Post by SeijiSensei on 2011-11-20
Maybe try using the full path to "twidge" in the script?

---

### Post by WasMeHere on 2011-11-20
As far as I understand, you initiate cron jobs in a different way for root. So you should not use crontab. Browse the internet for linux cron. I think you will find some good tutorial. You can also read the built-in manuals
```
man cron
man crontab
```
from man cron:
> ```
       cron also reads /etc/crontab, which is in a slightly  different  format
       (see  crontab(5)).
```
So you can edit /etc/crontab manually
```
sudo nano /etc/crontab
``` and you should ***not*** use sudo there.

For example:
```
# min hour dayofmonth month dayofweak   user  command
   *   *       *        *       *       root  fdisk -lu >/fdisk.txt
```
will write every minute the output of [FONT="Courier New"]fdisk -lu[/FONT] to the file [FONT="Courier New"]/fdisk.txt[/FONT] which is only allowed with superuser privileges.
[I]
Edit: **Leave whatever commands are in the /etc/crontab file, add your command as a line at the end of the file**[/I]

---

### Post by fdrake on 2011-11-20
agree with Olle Wiklund. Cron has 2 kinds of script users scripts and sys scripts (root priviledges). You cannot run root commands in the users cron scripts due to permissions issues.also notice that sys scripts requires you to specify the user you want to run the commands as (in this case root for you)
if you want to run your script you can save it as /etc/cron.intervel where interval is daily monthly, weekly etc.
ex /etc/cron.daily

---

### Post by McBraid on 2011-11-20
Tkans a lot!

There were two problems:
1. Full path was required for twidge.
2. Twidge needed to be configured for the user root.

Yey!

---

### Post by cog1 on 2012-03-25
Hi there

I'm trying to do the same thing, but much simpler for now.

Ubuntu Server 11.10 64bit.

Script /usr/local/twidge.cron

```
#!/bin/bash
date | /usr/bin/twidge update
```

sudo crontab -e:

```
* * * * * /bin/sh /usr/local/twidge.cron
```

This worked fine under a user account cron but I want to run it as root.   I re-authenticated twidge using sudo and confirm it's setup correctly; I can only now use twidge to update Twitter from the terminal if I'm root.

Now, when run manually this works fine:

```
sudo /bin/sh /usr/local/twidge.cron
```

The cron does not.  In the log:

```
CRON[17396]: (root) CMD (/bin/sh /usr/local/twidge.cron)
CRON[17395]: (CRON) error (grandchild #17396 failed with exit status 1)
CRON[17395]: (CRON) info (No MTA installed, discarding output)
```

Anyone have any suggestions?

Thanks

---

### Post by cog1 on 2012-03-25
Update.

Looks like I didn't actually setup twidge for the root account.  I changed the script to start with -x , and added an output to the cron job.

Error:  user error, no config file at /root/.twidgerc

I'll fix that, then I think it'll work fine.

---

