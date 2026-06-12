---
title: "cron.daily won't run?"
date: 2011-02-21
forum: Server Platforms
---

### Post by RuralHunter on 2011-02-21
Hi,

I'm with Ubuntu server 10.10. I created a script and put it in /etc/cron.daily. But looks it doesn't run(it didn't generate any log). The following is all I did. Did I miss anything?

```
root@chonseng1:/var/log# cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
root@chonseng1:/var/log# ls -l /etc/[cron.daily/ntpdate]("http://cron.daily/ntpdate")
-rwxr-xr-x 1 root root 52 2011-02-18 13:22 /etc/[cron.daily/ntpdate]("http://cron.daily/ntpdate")
root@chonseng1:/var/log# cat /etc/[cron.daily/ntpdate]("http://cron.daily/ntpdate")
 ntpdate [ntp.ubuntu.com]("http://ntp.ubuntu.com/") >>/var/log/ntpdate.log 2>&1

```

---

### Post by ashikaga on 2011-02-21
> **RuralHunter said:**
> 
```

test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

```

If /usr/sbin/anacron is present, then the statements in the parentheses will not be executed due to the OR operator. Is this related to your problem?

---

### Post by FuturePilot on 2011-02-22
I believe you need to specify a shell. It's also good technique to use fully paths in cron scripts.

```
#!/bin/sh
/usr/sbin/ntpdate ntp.ubuntu.com >>/var/log/ntpdate.log 2>&1
```

---

### Post by RuralHunter on 2011-02-22
> **ashikaga said:**
> If /usr/sbin/anacron is present, then the statements in the parentheses will not be executed due to the OR operator. Is this related to your problem?

/usr/sbin/anacron doesn't exist.

---

### Post by RuralHunter on 2011-02-22
> **FuturePilot said:**
> I believe you need to specify a shell. It's also good technique to use fully paths in cron scripts.

```
#!/bin/sh
 /usr/sbin/ntpdate [ntp.ubuntu.com]("http://ntp.ubuntu.com/") >>/var/log/ntpdate.log 2>&1
```
I will try this. thanks.

---

### Post by HermanAB on 2011-02-22
...and the script permissions must be made executable of course.

---

### Post by RuralHunter on 2011-02-22
> **FuturePilot said:**
> I believe you need to specify a shell. It's also good technique to use fully paths in cron scripts.

```
#!/bin/sh
 /usr/sbin/ntpdate [ntp.ubuntu.com]("http://ntp.ubuntu.com/") >>/var/log/ntpdate.log 2>&1
```
This works. thanks a lot!

---

### Post by RedScourge on 2011-05-03
This is NOT the cause of your particular problem, but I thought I'd mention this incase people  running into the issue I ran into come here, because this issue  messed me around for a few days!

Unlike some other systems like RedHat/Fedora/etc, run-parts under Debian  or Ubuntu systems will ignore files with dots or most other characters  in their name, meaning some or all of your scripts in run-parts folders  such as /etc/cron.daily will not be run. For example  /etc/cron.daily/backup.sh will never be run with the default way that  /etc/crontab is set up.

From man cron:

"Files must conform to the same naming convention as used by  run-parts(8): they must consist solely of upper- and lower-case letters,  digits, underscores, and hyphens. If the -l option  is specified, then  they must conform to the LSB namespace specification, exactly as in the  --lsbsysinit option in run-parts."

If you add the parameter --regex='(.*)' after run-parts in /etc/crontab then this should "fix" it however.

For example, in /etc/crontab:

Before:

1 * * * * root cd /tmp && run-parts --report /etc/cron.daily

After:

1 * * * * root cd /tmp && run-parts --regex='(.*)' --report /etc/cron.daily

---

