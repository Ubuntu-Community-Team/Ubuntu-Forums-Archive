---
title: "Postfix+SpammAssassin+ClamAV configuration"
date: 2009-03-18
forum: Server Platforms
---

### Post by trileru808 on 2009-03-18
Hello world,

I have a Dell R300 server running Ubuntu 8.10 Server. I have followed the how-to "Perfect Server 8.10 Ubuntu" and I installed ISPConfig with spamassassin, clamAV and postfix. At the moment everything is running great. Meaning...if i use the drop down menu for any user and select ON for SpamAssassin or antivirus they run great. My only problem is that i want to know how can I tweak the default settings for spamassassin and clamAV. I read some tutorials about integrating spamassasin into postfix, but i couldn't find anything in my postfix config file, even if spamassassin works perfect (eg it renames the subject with ***SPAM*** )

here is my master.cf file from postfix:

root@server1:/home/hackish# cat /etc/postfix/master.cf
#
# Postfix master process configuration file. For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ================================================== ========================
# service type private unpriv chroot wakeup maxproc command + args
# (yes) (yes) (yes) (never) (100)
# ================================================== ========================
smtp inet n - - - - smtpd
#submission inet n - - - - smtpd
smtps inet n - - - - smtpd
# -o smtpd_tls_security_level=encrypt
-o smtpd_sasl_auth_enable=yes
-o smtpd_client_restrictions=permit_sasl_authenticate d,reject
-o milter_macro_daemon_name=ORIGINATING
-o smtpd_tls_wrappermode=yes
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticate d,reject
# -o milter_macro_daemon_name=ORIGINATING
#628 inet n - - - - qmqpd
pickup fifo n - - 60 1 pickup
cleanup unix n - - - 0 cleanup
qmgr fifo n - n 300 1 qmgr
#qmgr fifo n - - 300 1 oqmgr
tlsmgr unix - - - 1000? 1 tlsmgr
rewrite unix - - - - - trivial-rewrite
bounce unix - - - - 0 bounce
defer unix - - - - 0 bounce
trace unix - - - - 0 bounce
verify unix - - - - 1 verify
flush unix n - - 1000? 0 flush
proxymap unix - - n - - proxymap
proxywrite unix - - n - 1 proxymap
smtp unix - - - - - smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay unix - - - - - smtp
-o smtp_fallback_relay=
# -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq unix n - - - - showq
error unix - - - - - error
retry unix - - - - - error
discard unix - - - - - discard
local unix - n n - - local
virtual unix - n n - - virtual
lmtp unix - - - - - lmtp
anvil unix - - - - 1 anvil
scache unix - - - - 1 scache
#
# ================================================== ==================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe( delivery
# agent. See the pipe( man page for information about ${recipient}
# and other message envelope options.
# ================================================== ==================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop unix - n n - - pipe
flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp unix - n n - - pipe
flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail unix - n n - - pipe
flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp unix - n n - - pipe
flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix - n n - 2 pipe
flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman unix - n n - - pipe
flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
${nexthop} ${user}

spamassassin config file is in:

root@server1:/home/hackish# cat /home/admispconfig/ispconfig/tools/spamassassin/etc/mail/spamassassin/local.cf
# This is the right place to customize your installation of SpamAssassin.
#
# See 'perldoc Mail::SpamAssassin::Conf' for details of what can be
# tweaked.
#
# Only a small subset of options are listed below
#
################################################## #########################

# Add *****SPAM***** to the Subject header of spam e-mails
#
# rewrite_header Subject *****SPAM*****


# Save spam messages as a message/rfc822 MIME attachment instead of
# modifying the original message (0: off, 2: use text/plain instead)
#
# report_safe 1


# Set which networks or hosts are considered 'trusted' by your mail
# server (i.e. not spammers)
#
# trusted_networks 212.17.35.


# Set file-locking method (flock is not safe over NFS, but is faster)
#
# lock_method flock


# Set the threshold at which a message is considered spam (default: 5.0)
#
# required_score 5.0


# Use Bayesian classifier (default: 1)
#
# use_bayes 1


# Bayesian classifier auto-learning (default: 1)
#
# bayes_auto_learn 1


# Set headers which may provide inappropriate cues to the Bayesian
# classifier
#
# bayes_ignore_header X-Bogosity
# bayes_ignore_header X-Spam-Flag
# bayes_ignore_header X-Spam-Status


seems like most options are disabled including 
# rewrite_header Subject *****SPAM*****
but, it is actualy working per user mode and i can select that from ispconfig. My question is: What file do I edit for tweaking spamassassin, since this one has the "rewrite_header" disabled, still it's using it ? I think clamav is in the same situation.

Thank you very much and have a nice day :)

---

### Post by volkswagner on 2009-03-18
Hi,

I have yet to impliment the following but my mail server is setup from the following how-to.

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

When you jump to the spamassasin section from the above link, it will refer you to the older how-to.  There you will find some helpful info on editing /etc/spamassassin/local.cf 

Direct jump.....  [http://flurdy.com/docs/postfix/edition5.html#conf_cont_spam](http://flurdy.com/docs/postfix/edition5.html#conf_cont_spam)

Hope it helps.

---

