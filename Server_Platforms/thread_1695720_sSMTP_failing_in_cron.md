---
title: "sSMTP failing in cron?"
date: 2011-02-26
forum: Server Platforms
---

### Post by MonkeyZiggurat on 2011-02-26
Hi, I hope someone can help me with this, here's the deal:

I've set up a reasonably simple script to transfer files from one folder to another for users to pickup via sftp. As part of the script, it checks for the existance of certain filenames and if it finds them, writes them to a file and calls sSMTP like this:

ssmtp -t < filelist.txt

before continuing with the rest of the operations.

This runs perfectly from the command line and I get the alert email straight away, but when scheduled in cron, the script never gets past the sSMTP stage.

I fount this in syslog that I think may be relevant:

Feb 26 15:00:02 nix01 CRON[16230]: (root) CMD (/scripts/sftptrans)
Feb 26 15:00:02 nix01 CRON[16228]: (root) MAIL (mailed 38 bytes of output but got status 0x0001#012)

If anyone has any ideas, I'd love to hear them.

Thanks

---

### Post by Cheesehead on 2011-02-26
Well, the two most common causes of cron failures are:
1) Didn't use full paths
2) Assumed an environment variable (like a user display)

Cron jobs run in a different (limited) environment to protect your system. While running off your Crontab will tell cron to use your user's permissions and where your user's /home directory is, it won't tell cron much else...like which tty or display you are using, or which groups you are in.

With cron jobs, assume the system is really stupid - explicitly declare *everything*.

If that doesn't help, then post the crontab and the script so we can reproduce it.

---

### Post by MonkeyZiggurat on 2011-02-26
Thanks for the reply, the contents of the script looks something like the below (I've taken out usernames and email addresses)

I'm no longer blaming ssmtp for this, as I got the same message in syslog when I commented out the ssmtp lines, and a similar lack of a positive result :(

```
#!/bin/sh



#-------------------------ALERT Email------------------------------

find /home/xxx/from_xxx/ -type f -name ra_\* > /var/notifications/remitFiles

                if [ -s "/var/notifications/remitFiles" ]; then

echo "To: My Email Address
From: Admin Email Address
Subject: Remittance Data

There are new remittance files.

" > /var/notifications/remitEmail

                        ssmtp -t < /var/notifications/remitEmail

                else

                echo "no remit files" > /var/notifications/remitEmail

               fi

#--------------------------OUTGOING--------------------------------


find /home/xxxtrans/to_xxx/DM -type f -exec cp {} /home/xxx/to_xxx/xx/ \; -exec rm {} \;

find /home/xxxtrans/to_xxx/DATA -type f -exec cp {} /home/xxx/to_xxx/DATA/ \; -exec rm {} \;

#--------------------------INCOMING--------------------------------

find /home/xxx/from_xxx/ -type f -name \*.txt -exec todos -epv {} \;

find /home/xxx/from_xxx/ ! -name from_xxx -type d -exec rsync -aqumh {} /home/xxxtrans/from_xxx/ \; -exec rm -r {} \;

find /home/xxx/from_xxx/ -maxdepth 1 -type f -exec rsync -aqumh {} /home/xxxtrans/from_xxx/ \; -exec rm {} \;
```

Cheers

---

### Post by MonkeyZiggurat on 2011-02-26
nevermind, turns out the problem was a missing mailx and nothing to do with the script or cron.

Thanks anyway!

---

