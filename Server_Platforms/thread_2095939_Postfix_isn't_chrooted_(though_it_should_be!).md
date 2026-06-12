---
title: "Postfix isn't chrooted (though it should be!)"
date: 2012-12-18
forum: Server Platforms
---

### Post by LSDave4Real on 2012-12-18
Hello,

[FONT=Arial][SIZE=2]Windows guy turned Linux newb here.  I have setup Ubuntu 10.04 and Postfix 2.7.0 to run as a secure smart-host, aka relay-server, aka SMTP-Gateway.  The host, named mail.myname.com, is located on a minimum-specs, remote virtual private server with a static IP.  It acts as primary MX server for two domains: myname.com and mybusiness.com.    [/SIZE][/FONT]

I successfully setup TLS encryption, and SASL authorization between mail.myname.com and the Exchange 2010 server on my LAN.   At present the setup functions, but not as securely as it should--especially for a SMTP server all alone on the Internet.  **First, I want to put Postfix in a chroot jail,** then I want to move away from using the "root" user, and then add antivirus and antispam.  This thread is about the chroot jail difficulties.

I've reviewed the Book of Postfix and several articles and posts online, and here's what I checked:

[LIST=1]
[*]The required file copies are in /var/spool/postfix--they were already there: I didn't do anything.
[*]The saslauthd folder and mux file are also in /var/spool/postfix/var/run/saslauthd--again, they were already there: I didn't do anything.
[*]The syslog socket is already in the postfix chroot at /var/spool/postfix/dev/log, as explained in a comment onctained in /etc/rsyslog.d/postfix.conf--again, they were already there: I didn't do anything.
[/LIST]
With all of that confirmed, I stopped postfix, turned on chroot in the master.cf, and started postfix.

Here is my master.cf (comments removed):
```
smtp      inet  n       -       y       -       -       smtpd
submission inet n       -       y       -       -       smtpd
smtps     inet  n       -       y       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
pickup    fifo  n       -       y       60      1       pickup
cleanup   unix  n       -       y       -       0       cleanup
qmgr      fifo  n       -       y       300     1       qmgr -v
tlsmgr    unix  -       -       y       1000?   1       tlsmgr
rewrite   unix  -       -       y       -       -       trivial-rewrite
bounce    unix  -       -       y       -       0       bounce
defer     unix  -       -       y       -       0       bounce
trace     unix  -       -       y       -       0       bounce
verify    unix  -       -       y       -       1       verify
flush     unix  n       -       y       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       y       -       -       smtp
relay     unix  -       -       y       -       -       smtp
        -o smtp_fallback_relay=
showq     unix  n       -       y       -       -       showq
error     unix  -       -       y       -       -       error
retry     unix  -       -       y       -       -       error
discard   unix  -       -       y       -       -       discard
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       y       -       -       lmtp
anvil     unix  -       -       y       -       1       anvil
scache    unix  -       -       y       -       1       scache
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
```I am under the impression that after restarting Postfix, it should now be running in a chrooted jail.  But the following commands suggest otherwise:
```
root@mail:/etc/rsyslog.d# postfix status
postfix/postfix-script: the Postfix mail system is running: PID: 2629
root@mail:/etc/rsyslog.d# ls -ld /proc/2629/root
lrwxrwxrwx 1 root root 0 2012-12-17 19:07 /proc/2629/root -> /

```This means postfix is running unchrooted, correct?  What am I missing?  How do I get postfix to run chrooted, please?

Thanks for your help.

---

### Post by LSDave4Real on 2012-12-19
Bump.

---

