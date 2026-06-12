---
title: "Sendmail problems, /var/log/mail.log &amp; postfix file details included: please help"
date: 2005-11-17
forum: Server Platforms
---

### Post by ytseshred on 2005-11-17
I posted a quesiton i'm having at the link below

[http://www.ubuntuforums.org/showthread.php?t=91607]("http://www.ubuntuforums.org/showthread.php?t=91607")

Further below, is the log error listed in /var/log/mail.log
```
Nov 17 16:23:39 localhost postfix/master[6458]: fatal: /etc/postfix/master.cf: line 84: bad hostname or network address: ::1:smtp
```

My /etc/postfix/main.cf is:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

# For better performance, chattr -S -R /var/spool/postfix, and use a
# journaled filesystem to achieve the same results as chattr +S gives.

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# Uncomment the next line to use procmail for delivery
#mailbox_command = procmail -a "$EXTENSION"


myhostname = localhost.localdomain
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = localhost.localdomain, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +

```

Hope this helps spawn some ideas for answers to my problem, which is that sendmail isn't sending any mail out.

---

### Post by Glut on 2005-11-17
4 Things:
1. It looks like your config file references an ip6 address and your not setup to support ip6. 
2. The error is in your /etc/postfix/master.cf and you posted your /etc/postfix/main.cf file.
3. Take both of these with a grain of salt, as I know a fair bit about sendmail, but not postfix. They are different programs, so I was a little confused by the subject.


4. A simple google search's first answer was this url: [http://www.linuxnotes.net/wiki.pl?PostfixServer](http://www.linuxnotes.net/wiki.pl?PostfixServer)
which provides this answer:
> 
Commenting out the following line in /etc/postfix/master.cf fixed it:

    ::1:smtp       inet n   -       -       -       -       smtpd


---

### Post by ytseshred on 2005-11-18
I had mentioned postfix, because in that how-to I found in the forums somewhere about setting up a mailserver, they seemed to be talking about postfix and sendmail as if sendmail depended on the postfix setup.  Also, the error in the mail.log pointed to postfix files, so...

Here's the /etc/postfix/master.cf: (I left out all the beginning comments)
```

# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
127.0.0.1:smtp inet n   -       -       -       -       smtpd
#::1:smtp       inet n   -       -       -       -       smtpd
#submission inet n      -       -       -       -       smtpd
#       -o smtpd_etrn_restrictions=reject
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       -       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp
relay     unix  -       -       -       -       -       smtp
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       n       -       -       lmtp
anvil     unix  -       -       n       -       1       anvil
#
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# maildrop. See the Postfix MAILDROP_README file for details.
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/local/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -d -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}

# only used by postfix-tls
#tlsmgr   fifo  -       -       n       300     1       tlsmgr
#smtps    inet  n       -       n       -       -       smtpd -o smtpd_tls_wrappermode=yes -o smtpd_sasl_auth_enable=y
es
#587      inet  n       -       n       -       -       smtpd -o smtpd_enforce_tls=yes -o smtpd_sasl_auth_enable=yes
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
scache    unix  -       -       -       -       1       scache
discard   unix  -       -       -       -       -       discard


```

---

### Post by ytseshred on 2005-11-18
Oh yea, the 
::1:smtp       inet n   -       -       -       -       smtpd
line wasn't originally commented out, I just did that now in repsonse to your post, and am restarting to test it...

---

### Post by ytseshred on 2005-11-18
It looks like it takes a while for the /var/log/mail.log file to get populated with errors, but here is what was put into it when I tried to sendmail to my gmail address from the command line:

I did:
```

prompt>  sendmail <myaddress>@gmail.com
             test message
             .
prompt>

```

```
Nov 18 10:47:16 localhost postfix/smtp[18325]: connect to gsmtp185-2.google.com[64.233.185.114]: Connection refused (port 25)
Nov 18 10:47:16 localhost postfix/smtp[18328]: connect to gsmtp185.google.com[64.233.185.27]: Connection refused (port 25)
Nov 18 10:47:16 localhost postfix/smtp[18325]: connect to gsmtp185.google.com[64.233.185.27]: Connection refused (port 25)
Nov 18 10:47:16 localhost postfix/smtp[18324]: 5B966A3960: to=<{myaddress}@gmail.com>, relay=none, delay=124421, status=deferred (connect to gsmtp83.google.com[66.249.83.27]: Connection refused)
Nov 18 10:47:16 localhost postfix/smtp[18327]: BAD49A3D4A: to=<{myaddress}@gmail.com>, relay=none, delay=33304, status=deferred (connect to gsmtp83-2.google.com[66.249.83.114]: Connection refused)
Nov 18 10:47:16 localhost postfix/smtp[18325]: 99675A3AA3: to=<{myaddress}@gmail.com>, relay=none, delay=117899, status=deferred (connect to gsmtp185.google.com[64.233.185.27]: Connection refused)
Nov 18 10:47:16 localhost postfix/smtp[18328]: 8C071A3A97: to=<{myaddress}@gmail.com>, relay=none, delay=202946, status=deferred (connect to gsmtp185.google.com[64.233.185.27]: Connection refused)

```

Any new ideas on what to try anyone?

---

### Post by Glut on 2005-11-21
It looks like the gmail server doesn't want to accept your connection. This could be caused by a variety of issues. You may have a setup issue that is disliked by the mail server, or you could have a firewall problem ,etc etc etc. 
First check that you can telnet out to servers: 
**telnet 123.123.123.123 25**
If you can't, most likely firewall issue.

---

