---
title: "Password Expire Notification"
date: 2009-03-16
forum: Security
---

### Post by hakras on 2009-03-16
I am in need of a way to notify users when their password or account will expire.  In my environment, users are running an application that automatically logs into their Ubuntu account.  Therefore, users do not physically see the password or account expires warning messages.  I need to find a way (script) to run a daily task that will check the password expiration and account expiration.  If either is 14 days or less to expire, send them and an admin account an e-mail.

I could do this in Windows, but have no clue how to do this in Ubuntu.  Does anyone know how this can be done?

---

### Post by telemusic on 2009-03-18
#!/bin/bash

sec=`date +%s`
let min=$sec/60
let hr=$min/60
let day=$hr/24

#$day = number of days since 1970-01-01


for i in `ls /home` #for each user from your server
do
chday=`cat /etc/shadow | grep $i | cut -d ":" -f 3`
let dif=$day-$chday 

#$chday = day (counted from 1970-01-01) of last password change
#$dif = number of days since last password change


if [ "$dif" -gt 30 ]     #if password was changed more than 30 days ago
then
# here put some actions that will notify user, that he should change password - I use sendEmail, #to send mail notify
fi
done



And then put this script in crontab, to run it daily.

---

### Post by hakras on 2009-03-24
I have run into an issue.  I cannot send mail from this segment of the network.  I've planned a work around.  What I am looking to do is output the information from the script above to a text file.  What would be the command to write the results to a file?

Thanks

---

