---
title: "sendmail goes to wrong address when triggerd by cron"
date: 2010-03-17
forum: Server Platforms
---

### Post by ofrxnz on 2010-03-17
So, I wrote/cobbled-together this nifty sendmail script to read some logs and take some disk stats.  basically i'm reporting on rsnapshot.  

When I run it as 
```
sudo /etc/rsnapshot/mailSta.sh
```
Everything works wonderful and the emails arrive as expected and fires off an email to two accounts at a remote server

Syslog lines
> Mar 17 09:19:31 SERVER postfix/pickup[4205]: C96EE6095A: uid=0 from=<root>
Mar 17 09:19:31 SERVER postfix/cleanup[5126]: C96EE6095A: message-id=<20100317131931.C96EE6095A@SERVER.domain.tld>
Mar 17 09:19:31 SERVER postfix/qmgr[12739]: C96EE6095A: from=<root@SERVER.domain.tld>, size=1797, nrcpt=2 (queue active)
Mar 17 09:19:32 SERVER postfix/smtp[5130]: C96EE6095A: to=<RealEmail1@domain.com>, relay=mail.domain.com[192.168.5.3]:25, delay=0.4, delays=0.08/0.06/0.06/0.21, dsn=2.6.0, status=sent (250 $
Mar 17 09:19:32 SERVER postfix/smtp[5130]: C96EE6095A: to=<RealEmail2@domain.com>, relay=mail.domain.com[192.168.5.2]:25, delay=0.4, delays=0.08/0.06/0.06/0.21, dsn=2.6.0, status=sent (250 $
Mar 17 09:19:32 SERVER postfix/qmgr[12739]: C96EE6095A: removed


When I have a cron job fire it off as a cron job it goes to the local admin user on the local server and not the addresses specified.

```
 00 09          * * *           root    /etc/rsnapshot/mailStatistics.sh
```

> Mar 17 14:30:01 SERVER /USR/SBIN/CRON[9625]: (root) CMD (/etc/rsnapshot/mailStatistics.sh)
Mar 17 14:30:01 SERVER postfix/pickup[9278]: BC3E16095A: uid=0 from=<root>
Mar 17 14:30:01 SERVER postfix/cleanup[9645]: BC3E16095A: message-id=<20100317183001.BC3E16095A@server.domain.tld>
Mar 17 14:30:01 PRIDCVX-BAC01 postfix/qmgr[12739]: BC3E16095A: from=<root@server.domain.tld>, size=635, nrcpt=1 (queue active)
Mar 17 14:30:01 PRIDCVX-BAC01 postfix/local[9647]: BC3E16095A: to=<localSystemUser@THIS SERVER NOT MAIL SERVER>, orig_to=<root>, relay=local, delay=0.11, delays=0.05/0.01/0/0.05, dsn=2.0.0, status=sent (delivered$
Mar 17 14:30:01 SERVER postfix/qmgr[12739]: BC3E16095A: removed


Here is the mail script

```
#!/bin/bash
#requires: date,sendmail
function fappend {
    echo "$2">>$1;
}
YYYYMMDD=`date +%Y%m%d`

# CHANGE THESE
TOEMAIL="RealEmail1@domain.com,RealEmail2@domain.com";
FREMAIL="backup@domain.tld";
SUBJECT="Daily Backup Report - $YYYYMMDD";
MSGBODY="This is your daily backup notice.  This message provides information about the the daily sucesses and failures the linux backup server had sucking down files.  This message does not (yet) verify th$

#####my bits##########
#logfile
logfile="/var/log/rsnapshot.log"
# temp log file
tmplog="/tmp/tmprslog"
# extract todays log ( format 30/Mar/2006 )
fgrep `date +"%d/%b/%Y"` $logfile >$tmplog
BUMESSAGES=$( egrep "completed|ERROR" $tmplog ;)
########################

# DON'T CHANGE ANYTHING BELOW
TMP="/tmp/tmpfil_123"$RANDOM;

rm -rf $TMP;
fappend $TMP "From: $FREMAIL";
fappend $TMP "To: $TOEMAIL";
fappend $TMP "Reply-To: $FREMAIL";
fappend $TMP "Subject: $SUBJECT";
fappend $TMP "";
fappend $TMP "$MSGBODY";
fappend $TMP "";
#####my bits #####
#add log messages
fappend $TMP "$BUMESSAGES"
fappend $TMP "";
fappend $TMP "";
fappend $TMP "";
fappend $TMP "Some file system usage statistics: ";
fappend $TMP "";
# add usage stats
for F in $(find /etc/ -name rsnapshot*.conf;)
do
duDat=$(/usr/bin/rsnapshot -c $F du ;)
fappend $TMP "$duDat";
duDat=
fappend $TMP "";
done
####################
fappend $TMP "";
fappend $TMP "";
cat $TMP|sendmail -t;
rm $TMP;

```

Any Ideas are greatly appreciated.

Thanks in advance

Adam

P.S. the logs and scripts are slightly edited so as not to reveal anything more than is needed about the setup

---

### Post by KB1JWQ on 2010-03-17
Does your system think it's supposed to receive mail for domain.com?

You may also look into whether or not there's anything that shows up in "env" when you send it from shell, like an environment variable that's not getting passed to your script.

---

