---
title: "disk size notification"
date: 2010-12-12
forum: Server Platforms
---

### Post by rbalaa on 2010-12-12
Hello All,

Anyone of a tool/script that will alert me when my server has reached a certain disk size. I run nightly backups and would like to monitor this.

Thanks in advance.

---

### Post by rubylaser on 2010-12-12
I just would write a simple shell script to check your disk space everyday.  This would email you when you get to 10% remaining.

```
mkdir -p /root/scripts/
vi /root/scripts/diskAlert
```

and paste this in...

```
#!/bin/sh
df -H | grep -vE '^Filesystem|none|cdrom' | awk '{ print $5 " " $1 }' | while read output;
do
  echo $output
  usep=$(echo $output | awk '{ print $1}' | cut -d'%' -f1  )
  partition=$(echo $output | awk '{ print $2 }' )
  if [ $usep -ge 90 ]; then
    echo "Running out of space \"$partition ($usep%)\" on $(hostname) as on $(date)" |
     mail -s "Alert: Almost out of disk space $usep%" youremailaddress@gmail.com
  fi
done
```

Then, make add an entry to your root crontab to run this daily...
```
10 0 * * * /root/scripts/diskAlert
```

Hope that helps.

---

### Post by rbalaa on 2010-12-12
Great. Thanks. I will try this.

---

### Post by TwiceOver on 2010-12-12
That script probably relies on you running an email server. If you just want to use an external account, do a google search for sendemail peel script. I use this script to send me a server performance report daily and in case of errors, send me a text message.

---

### Post by rbalaa on 2010-12-12
> **TwiceOver said:**
> That script probably relies on you running an email server. If you just want to use an external account, do a google search for sendemail peel script. I use this script to send me a server performance report daily and in case of errors, send me a text message.

Yes, I have postfix relaying my mail via an external mail server. thanks.

---

