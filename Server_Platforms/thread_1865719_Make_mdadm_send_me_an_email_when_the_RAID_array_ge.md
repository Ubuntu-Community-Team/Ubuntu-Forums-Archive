---
title: "Make mdadm send me an email when the RAID array gets degraded"
date: 2011-10-20
forum: Server Platforms
---

### Post by X1R1 on 2011-10-20
How can I do this? If I input the command:

sudo mdadm --monitor /dev/md0 -t -1

mdadm: Monitor using email address "myemail@mydomain.com" from config file
sendmail: fatal: open /etc/postfix/main.cf: No such file or directory

I dont want to configure a full blown mail server just to do this, what approach can I take?

thanks in advance

---

### Post by rubylaser on 2011-10-20
You need to edit add the email line to your mdadm.conf file, and then I normally just setup sSMTP and send emails via my Gmail account.

[http://www.nixtutor.com/linux/send-mail-with-gmail-and-ssmtp/]("http://www.nixtutor.com/linux/send-mail-with-gmail-and-ssmtp/")

---

### Post by X1R1 on 2011-10-20
Exactly what I was looking for! thanks a lot! one more question though, once I setup this part of email the mdadm email will email me automatically to the address I tell it to? Since I only ran a test how do I make this command run at every boot? will adding this line to cron help?

mdadm --monitor --mail=myemail@mydomain.com --delay=1800 /dev/md0

or should I add it somewhere else?

thanks for the help!

---

### Post by rubylaser on 2011-10-20
Run, this (replace the email address with yours)
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Then, run
```
dpkg-reconfigure mdadm
```

Reboot, and you should see mdadm monitor in dmesg or if you do this
```
ps aux | grep mdadm
```

Finally, you can run this from the command line to test the email is working...
```
mdadm --monitor --scan --test
```

---

