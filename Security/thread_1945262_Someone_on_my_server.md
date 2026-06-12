---
title: "Someone on my server?"
date: 2012-03-22
forum: Security
---

### Post by ubudog on 2012-03-22
Hello all, I may be a bit paranoid but I saw this in auth.log on my server.
```
Successful su for amavis by root
+ ??? root:amavis
```

Does this look suspicious to someone more knowledgeable on this? 

Thanks for any help!
- ubudog

---

### Post by MasterGamerJK on 2012-03-22
It _appears _to be related to some type of malware....

Check this: 

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)


You could also check /home/ to check for additional user accounts.

---

### Post by Ms. Daisy on 2012-03-22
Dunno about the "more knowledgeable" part, but is it an email server? And are you running amavis content filtering for spam/anti-virus?  What was going on in the other logs at that time?

---

### Post by ubudog on 2012-03-22
Doesn't seem to be anything weird in /home.  :-/

---

### Post by ubudog on 2012-03-22
> **Ms. Daisy said:**
> Dunno about the "more knowledgeable" part, but is it an email server? And are you running amavis content filtering for spam/anti-virus?

I was running it as a mail server for a bit, though I got rid of postfix, dovecot, and everything else I was running.  Now that I think about it, I forgot to uninstall amavis.

> **Ms. Daisy said:**
> What was going on in the other logs at that time?  

Know of any other logs I should check?  

Thanks for the help!  :)

---

### Post by CharlesA on 2012-03-22
Check the auth.log for any other entries, but it's likely that the box was owned.

Check out the link to "Did I get owned" in Ms. Daisy's sig for some helpful info to see if your box was compromised or not.

---

### Post by Ms. Daisy on 2012-03-22
I would suspect an automatic update, cron job, something like that for amavis. 

Follow Dangertux's Did I Get Owned guide (in my sig).

---

### Post by CharlesA on 2012-03-22
> **Ms. Daisy said:**
> I would suspect an automatic update, cron job, something like that for amavis. 

Follow Dangertux's Did I Get Owned guide (in my sig).
I saw something about it here:
[https://help.ubuntu.com/community/PostfixAmavisNew](https://help.ubuntu.com/community/PostfixAmavisNew)

But it doesn't sound familiar to me.

---

### Post by ubudog on 2012-03-23
Thanks for the help, I have reinstalled Ubuntu and have it locked down now.

Ms. Daisy:  that's a great read, thanks!

---

### Post by Ms. Daisy on 2012-03-23
Glad you got it resolved. Did the other logs indicate it got owned?

---

### Post by ubudog on 2012-03-23
> **Ms. Daisy said:**
> Glad you got it resolved. Did the other logs indicate it got owned?

Not really; I checked those listed by 'Did I Just Get Owned', and all looked normal.  All that was weird was auth.log.  :-/

---

### Post by Ms. Daisy on 2012-03-23
Better safe than sorry.  Plus with a reinstall you got rid of any other left-overs from the email server days.

---

### Post by ubudog on 2012-03-23
> **Ms. Daisy said:**
> Better safe than sorry.  Plus with a reinstall you got rid of any other left-overs from the email server days.

Yep, and I blocked all ports except 22 and 80 (the only ones I really need), so I think we're good now.

---

### Post by CharlesA on 2012-03-23
> **ubudog said:**
> Yep, and I blocked all ports except 22 and 80 (the only ones I really need), so I think we're good now.
Indeed. :)

---

### Post by bubylou on 2012-03-23
Make sure to take all the necessary security measures to secure the services listening of those ports.  Especially 22 ssh. Key authentication, limit access, etc.

---

### Post by goebeler on 2012-10-18
just in case someone else stumbles across this thread.. I've had the same mysterious entry in my auth.log and I as far as I can tell it is NOT something evil ;)
when I saw that entry I checked when and how often it occures and I found that appeared exactly every 24h...

looked like a cron job to me... so I checked /etc/cron.daily and found a script named 

```
amavisd-new
```which containes:

```

#!/bin/sh
#
#  Daily maintenance for amavisd-new
#  $Id: amavisd-new.cron.daily 930 2006-08-10 13:38:45Z hmh $
# 
test -e /usr/sbin/amavisd-new-cronjob && exec /usr/sbin/amavisd-new-cronjob sa-clean
exit 0
```looks like a normal maintance script to me... but to be sure I checked the content of 
```
 /usr/sbin/amavisd-new-cronjob
```take a look:

```
#!/bin/sh

# amavisd-new cronjob helper
#
# Run it as root or as the amavis user
#
# First parameter specifies which cronjob routine to run:
#         sa-sync:    spamassassin fast sync
#         sa-clean:    spamassassin cleanup

test -e /usr/bin/sa-learn || exit 0
test -e /usr/sbin/amavisd-new || exit 0

SUUSER="amavis"

set -e
umask 022

# WATCH OUT FOR PROPER QUOTING LEVEL WHEN CALLING THIS!
do_amavis_cmd() {
    if [ "$(id -u -n)" != "${SUUSER}" ]; then
        exec /bin/su -s /bin/sh - "${SUUSER}" -c "$*" >/dev/null
    else
        # to get the same quoting level as the su path
        CMD="$*"
        exec ${CMD} >/dev/null 
    fi
}

case $1 in
    sa-sync)
        do_amavis_cmd "/usr/bin/sa-learn --sync"
        ;;
    sa-clean)
        do_amavis_cmd "/usr/bin/sa-learn --sync --force-expire"
        ;;
    *)
        echo "$0: unknown cron routine $1" >&2
        exit 1
        ;;
esac

exit 0

```basically what it does is su-ing to the amavis user and calling a spamassasin cleanup method... so really .. nothing too evil ;)

---

### Post by thomasw81 on 2012-11-26
@goebeler:

Since a few days I also noticed the same in one of my email server logs:

Successful su for amavis by root
+ ??? root:amavis 2012

It  is called by a cron job and seems to be related to a cleanup, as you stated. 

The  strange thing is that I have been running amavis for about a year on  this machine, and suddenly since last week I get this message in the  auth.log every day at the same time.

I posted on the amavis mailing list, but my message is still under moderation.. I didn't notice any updates for amavisd-new, so I am not quite reassured as to why it is running daily.. I do have a script in cron.daily though.

---

