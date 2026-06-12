---
title: "cron jobs in auth.log"
date: 2006-01-31
forum: Server Platforms
---

### Post by mtron on 2006-01-31
hi! 

my auth.log file of the server hows masses of cron jobs:

```
Jan 31 15:17:01 palestine CRON[6287]: (pam_unix) session opened for user root by (uid=0)
Jan 31 15:17:01 palestine CRON[6289]: (pam_unix) session opened for user www-data by (uid=0)
Jan 31 15:17:01 palestine CRON[6287]: (pam_unix) session closed for user root
Jan 31 15:17:01 palestine CRON[6289]: (pam_unix) session closed for user www-data
Jan 31 15:18:01 palestine CRON[6302]: (pam_unix) session opened for user www-data by (uid=0)
Jan 31 15:18:01 palestine CRON[6302]: (pam_unix) session closed for user www-data
Jan 31 15:19:01 palestine CRON[6324]: (pam_unix) session opened for user www-data by (uid=0)
Jan 31 15:19:01 palestine CRON[6324]: (pam_unix) session closed for user www-data
Jan 31 15:20:01 palestine CRON[6340]: (pam_unix) session opened for user www-data by (uid=0)
Jan 31 15:20:01 palestine CRON[6340]: (pam_unix) session closed for user www-data
Jan 31 15:21:01 palestine CRON[6352]: (pam_unix) session opened for user www-data by (uid=0)
```

i don't really understand what's going on there. how con i check the cron job with this number? i don't thinnk that this is normal, so any advice how to secure the system would be great.

i have an SSH: IP restriction in my hosts.allow file. is the same possible for 

FTP:  IPs

to restrict the ftp access to fixed ip's similar to SSH? 

thanks!

---

### Post by olddog55 on 2006-01-31
The auth.log messages are normal and created by the pam module.

It would seem you have a cron job running every minute under the 'www-date' userid.

Check the system and www-data user cron jobs to determine what's running:
 sudo crontab -u www-data -l
 sudo cat /etc/crontab

/d

---

### Post by mtron on 2006-02-01
thanks. it seems that there is a cron job running to backup the empty /var/tmp directory once in a minute:

```
$ sudo crontab -u www-data -l

*/1 * * * * '/var/tmp/..   /monitor'
```

and 
```
sudo cat /etc/crontab

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cro n.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cro n.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cro n.monthly

```

i have only worked with webmin till now. how can i delete this unuseful cron job?

I'm so paranoid, cause this server got hacked some days ago (now i changed the SSH port number,  restricted all ssh access hosts.deny ALL: ALL, and hosts.allow ALL: my IP, this should prevent any further trouble)

the script kiddie installed a php code in the /var/www directory to use this machine as a spam outlet and i am checking now if he did something else (with the auth.log file)

---

### Post by MJN on 2006-02-01
If I were you, and had been hacked, I'd start afresh with a compelte re-install. IMHO attempting to clear up now is a akin to locking the stable door once the horse has already bolted... Better to knock the stable down and build a new one.. ;) (who knows what else he's done that you don't know about?)
 
Mathew

---

### Post by Glut on 2006-02-01
I strongly agree with MJN. If you've been hacked, you may never know what nasties are still on your system - you have changed ssh, but a backdoor may have been installed elsewhere.
The only safe option is to wipe and reinstall. Also, you should restore all your data from a backup that you **know** was before the hack. You make backups, right? :-)

---

### Post by olddog55 on 2006-02-01
I concur.   The cron job appears to be a hacker dropping.  

No normal program would use a directory named '..   '  [ as in dot-dot-space-space-space ]  which is what is in your crontab.
Look at that cronjob again:  The hard quote (') makes the spaces part of the name.

To delete the cronjob:  sudo rm /var/spool/cron/crontabs/www-data
To delete the bogus directory:  sudo rm -f /var/tmp/..?*
    ( Which will remove *all* directories and their contents named /var/tmp/[dot-dot-any_character-anything] )

WARNING:  Anytime you do a 'sudo rm', or any other sudo command for that matter, make sure you understand what you are doing.  You can ruin your system.   

If you're *really* curious, take the box off the wire and examine the contents of the 'monitor' program in the '/var/tmp/[dot-dot-space-space-space]' directory...

Your best course of action:  Copy off any needed data to a floppy or other system and fully rebuild your system. 

/d

---

### Post by mtron on 2006-02-02
Thanks gyus for your advices! 

The thing is it's not my server, but from a friend i did the website for (i told him to install ubuntu on this machine back in warty times) who asked me to fix it after the hack, and the server is 3000 km  away from me, so no physical access possible.

the good thing is that the hacker used sudo, so every step he did was perfectly tracked in the auth.log (every sudo command gets logged there) so it was actually quite easy to "undo".

Untill the cron jobs. he used a cgi script in the /var/tmp dir for his spam outlet and changed the httpd.conf a bit, so i just uninsalled all the services  (incl. configuration settings)   upgraded to the urrent release and satred with a new setup.

But the cron jobs were still there.

---

### Post by MJN on 2006-02-02
[quote=mtron]the good thing is that the hacker used sudo, so every step he did was perfectly tracked in the auth.log (every sudo command gets logged there) so it was actually quite easy to "undo".[/quote]
 
Given he had su privileges what makes you think he didn't remove the entries pertaining to really sneaky things from auth.log?
 
You've got to face the music - the compromise means you cannot trust the current state the machine is in - any assumption on your part as to what did or didn't happen merely introduces uncertainties in exactly how 'secure' you now are...
 
Start afresh - you know it makes sense.
 
Mathew

---

### Post by mtron on 2006-02-02
Dam you're right. didn't think about this at all. D'ohh

Ok, i will start over with a new install, but thanks anyway. this time i will take the security much more serious. 

i just read that the next release will be supported for 5 years on servers. [https://wiki.ubuntu.com/DapperGoals](https://wiki.ubuntu.com/DapperGoals)

---

