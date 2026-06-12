---
title: "Permission denied /usr/bin/maildrop"
date: 2009-07-27
forum: Server Platforms
---

### Post by RobJohnston on 2009-07-27
Hi all, I have a VPS with Ubuntu 9.04. I've setup ISPConfig etc as per the Perfect Server Howto Forge pages.

However I'm getting a problem with the configuration of maildrop, I get
temporary failure. Command output: ERR: authdaemon: s_connect() failed: Permission denied /usr/bin/maildrop: Unable to change to home directory.

I've check the permissions: 755 /var/vmail

Most of the examples I've found on Google of this error have permission problems, can anyone suggest another direction of investigation?

Cheers, Rob.

---

### Post by jhannah on 2009-07-27
Assuming you are still running maildrop under the default vmail user, what do the below commands give you:

ls -lah /var/vmail
grep vmail /etc/passwd

It sounds like the problem lies with the ownership and/or permissions on the home directory for the vmail user. You should be able to chown -R the vmail user's home directory and resolve the errors you are seeing but if that isn't the problem, let me know.

---

### Post by RobJohnston on 2009-07-27
Hi there, here's the output
ls -lah /var/vmail
drwxr-xr-x  4 vmail vmail 4.0K Jul 27 04:19 .
drwxr-xr-x 15 root  root  4.0K Jul 26 13:01 ..
-rw-------  1 vmail vmail 1.3K Jul 26 13:01 .mailfilter
drwxr-xr-x  5 vmail vmail 4.0K Jul 26 17:15 siricom.co.uk
-rw-rw----  1 vmail vmail    4 Jul 27 04:19 ispconfig_mailsize
drwxr-xr-x  2 root  root  4.0K Jul 26 13:01 mailfilters

root@rjohnston:/# grep vmail /etc/passwd
vmail:x:5000:5000::/home/vmail:/bin/sh

The folder permission and ownership seem to be OK.

---

### Post by pot_roast on 2010-04-04
Kind of an old thread, I know, but the problem is probably with the maildrop binary itself.

Seems that maildrop no longer has authlib support (BAD!!!) and it needs to be setuid root (chmod u+s /usr/bin/maildrop) to get around that permission denied error.

That just leads to other problems, unfortunately. You'll probably need to recompile your own version with mysql support and authlib support. This seems easier said than done, however.

---

### Post by colinmb on 2010-07-13
I have a similar problem. I'm getting mail with fetchmail (via a user cron job), and it's delivered to ~/.maildir via maildrop. For some reason, I see the same error message (ERR: authdaemon: s_connect() failed: Permission denied), but the mail gets delivered successfully.

maildrop permissions:
```
colin@home:~$ ls -l /usr/bin/maildrop
-rwxr-sr-x 1 root mail 174168 2010-02-02 00:56 /usr/bin/maildrop
```In postfix master.cf:
```
colin@home:~$ grep -A 1 ^maildrop /etc/postfix/master.cf
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
```When I run fetchmail:
```
fetchmail: about to deliver with: /usr/bin/maildrop -d 'colin'
#*ERR: authdaemon: s_connect() failed: Permission denied
```It's nice that my mail is getting delivered, but I'd certainly like to fix this error. Any ideas? Could there be an issue because of the fact that this "vmail" user is referenced but my system only has a "mail" user?

EDIT: I found that I can induce this problem by simply running maildrop from the command line:

```
colin@home:~$ maildrop -d 'colin'
ERR: authdaemon: s_connect() failed: Permission denied
```I then ran an strace on the same command, and came across the apparent cause of the error message:

```
connect(3, {sa_family=AF_FILE, path="/var/run/courier/authdaemon/socket"}, 110) = -1 EACCES (Permission denied)
```Indeed, the /var/run/courier/authdaemon/ directory is root:root (drwxr-x---). Is that incorrect? What's going on here?

--Colin

---

### Post by colinmb on 2010-10-19
As a simple workaround for this permissions issue, add the following to /etc/rc.local:

```
chmod 755 /var/run/courier/authdaemon
```

--Colin

---

