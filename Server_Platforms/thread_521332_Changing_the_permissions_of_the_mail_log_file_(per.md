---
title: "Changing the permissions of the mail log file? (permanently)"
date: 2007-08-09
forum: Server Platforms
---

### Post by MJN on 2007-08-09
Can anyone tell me how to change the permissions of the mail log file such that it can be world readable?

The current permissions are:

-rw-r----- 1 root adm 854580 2007-08-09 14:51 /var/log/mail.log
 
If I try to set the world-readable flag it only persists until a new file is created when syslog does its rotations. Hence, I guess I'm actually asking how to define the permissions for new logs created by syslog?

The rationale behind the question/intent is that I want to symlink to the mail log from a file within my web space to enable me to view the mail log remotely (through a browser as opposed to SSHing in). Naturally this particular area of the web space is suitably protected with authentication and SSL.

Can anyone advise any reasons why I shouldn't be doing this? Of course, one solution would be to make www-data part of the adm group but that's obviously not a good idea hence this post for other ideas?

Thanks,

Mathew

---

### Post by Coops on 2008-01-25
I'm looking for a solution to this too.

Any ideas?

---

### Post by tlcoffee on 2008-01-25
the mail.log is handled by the syslog and its rotated by cron. In your /etc/cron.weekly/sysklogd you _could_ do the following:

Look for:

```
for LOG in $logs
do
   if [ -s $LOG ]; then
      savelog -g adm -m 640 -u ${USER} -c 4 $LOG >/dev/null
   fi
done

```Replace with:

```

for LOG in $logs
do
if [ ! $LOG = "mail.log" ] && [ -s $LOG ]; then
      savelog -g adm -m 640 -u ${USER} -c 4 $LOG >/dev/null
else
      savelog -g adm -m 644 -u ${USER} -c 4 $LOG >/dev/null
fi
done

```

---

### Post by MJN on 2008-01-25
Nice!
 
Unfortunately I don't need it anymore but hopefully it'll be good for Coops (and a lesson learnt for me too on this type of problem).
 
Mathew

---

