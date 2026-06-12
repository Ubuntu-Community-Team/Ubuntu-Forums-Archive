---
title: "Configuring CyberPower/pwrstatd for email alerts?"
date: 2016-03-01
forum: Server Platforms
---

### Post by Scrumps on 2016-03-01
Hello, 

I have installed the software directly from CyberPower, however, it seems there is an issue with their bash script, and I am not entirely great and coming up with and determining the causes for issues with bash scripts. With that said, I am using ssmtp, since /etc/mail.rc does not eixst on a stock ubuntu server install (or if it did, it doesn't on mine).

When one of the scripts tries to run, it receives the following:

> /etc/pwrstatd-email.sh: 23: [: !=: unexpected operator
/etc/pwrstatd-email.sh: 27: /etc/pwrstatd-email.sh: Syntax error: "(" unexpected


cat /etc/pwrstatd-email.sh 
```
#
# This is sample script of the send mail for pwrstatd daemon using.
#


#!/bin/sh


# If you want to change SMTP server, edit following parameters into /etc/mail.rc file.
# set smtp=smtp server address
# set smtp-auth-user=user name
# set smtp-auth-password=user password




SUBJECT="PowerPanel Notification - [$EVENT]"
FROM="PowerPanel Daemon <$SENDER_ADDRESS>"
TO="$RECEIPT_NAME <$RECEIPT_ADDRESS>"
MESSAGE="Warning: The $EVENT event has occurred for a while, system will be shutdown immediately!"


DATE=`date +'%Y/%m/%d %p %H:%M'`
test ${#DATE}


RUNTIME=""


if [ $REMAINING_RUNTIME != none ]; then
        RUNTIME="Remaining Runtime: $REMAINING_RUNTIME Seconds"
fi


DATA=(
"========================================================"
"   $SUBJECT"
"========================================================"
""
""
"$MESSAGE"
"Time: $DATE"
""
""
"UPS Model Name: $MODEL_NAME"
"Battery Capacity: $BATTERY_CAPACITY %"
"$RUNTIME"
)


IFS=$'\n'
echo "${DATA
[*]}" | mail \
-r   "$FROM" \
-s   "$SUBJECT" \
     "$TO"


exit 0




```

Just to help out this is line 22 and line 27:
22:if [ $REMAINING_RUNTIME != none ]; then
27:DATA=(


How can I go about resolving this, so that I can send emails? It would be nice to know when my server goes down, at least. As that is my last line of defense. Thankfully, almost all of my startup services work, so it isn't a huge issue, but I would like to gracefully shut the machine down, rather than have the power just shut off.

---

### Post by gordintoronto on 2016-03-02
Do you have a mail server on your server?

---

