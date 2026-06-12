---
title: "Is Postfix eating Spamassassin mail?"
date: 2008-05-30
forum: Server Platforms
---

### Post by jbbarnes on 2008-05-30
I installed a very basic Ubuntu 7.11 server, including the Postfix and spamassassin options. I know that spamassassin is working because I can see the modified headers in user e-mails picked up by their POP3 e-mail clients.

I have made basically no changes to the spamassassin local.cf file. It is just set to rewrite the header when the score reaches 5.0. But what actually happens is that such messages never get delivered to the user. They just seem to disappear.

I have spent hours inspecting and tweaking spamassassin and am convinced it is configured correctly. Is there perhaps some setting in Postfix that is part of the default Ubuntu server configuration that discards or reroutes messages spamassassin flags? 

(I have made only the barest of configuration changes to this system, along the lines of setting the IP and hostname, etc. That was the selling point of Ubuntu server--that it was so well configured out of the box and I didn't want to change it.)

Thanks for any help you can provide.

---

### Post by Monicker on 2008-05-30
I've never seen anything in postfix alone which would drop a message just because it had spamassassin headers.  My first thought is that there is a configuration problem with /etc/postfix/master.cf, which is not letting it send the message on after spam assassin has done content filtering.

Please post the contents of /etc/postfix/master.cf

---

### Post by jbbarnes on 2008-05-30
Thanks. Here is my master.cf (with long commented sections removed for brevity). I don't think I altered this from the standard configuration.

[FONT="Courier New"][SIZE="2"]# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_enforce_tls=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
	-o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache	  unix	-	-	-	-	1	scache

#
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}[/SIZE][/FONT]

---

### Post by Monicker on 2008-05-30
Hrmm. How are postfix and spamassassin communicating with each other?  I don't see any references in your config for spamassassin at all.

The I've done it myself is to have master.cf redirect the traffic to amavisd or spamassassin and then have it passed back to postfix.

Something along the lines of what is shown here:
[http://www.debuntu.org/postfix-and-pamassassin-how-to-filter-spam-p2]("http://www.debuntu.org/postfix-and-pamassassin-how-to-filter-spam-p2")

---

