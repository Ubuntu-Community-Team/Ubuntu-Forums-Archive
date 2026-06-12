---
title: "postfix couldn't take the update"
date: 2009-12-26
forum: Server Platforms
---

### Post by snake_eyes on 2009-12-26
Hello,

I wanna retrieve mails from external mail server via fetchmail and deliver them to postfix, I follow [http://www.postfix.org/VIRTUAL_README.html#virtual_mailbox](http://www.postfix.org/VIRTUAL_README.html#virtual_mailbox) but it still deliver the mails to the /var/mail/user, also I check this [http://forums.freebsd.org/showpost.php?p=43655&postcount=10](http://forums.freebsd.org/showpost.php?p=43655&postcount=10) and all the configuration are correct but it still deliver the mails to the postfix to the wrong path :(

here is mail main.cf
> 
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = admin-laptop
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = admin-laptop, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

virtual_mailbox_domains = domain.com
virtual_mailbox_base = /var/mail/vhosts
virtual_mailbox_maps = hash:/etc/postfix/vmailbox
virtual_minimum_uid = 100
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_alias_maps = hash:/etc/postfix/virtual


Any help please...

Cheers,

---

### Post by noway2 on 2009-12-26
I am sorry, but I am not fully understanding what you are trying to do, or rather what your problem is.  I gather that postfix is delivering mail, but to the wrong place?  Postfix will deliver according to the setting for mydestination.  According to your setup, you appear to have a set of hash tables that define the mapping from the virtual hosts to the mailbox/maildir location.  It sounds like you need to look into how these are set up.

---

### Post by snake_eyes on 2009-12-26
> **noway2 said:**
> I am sorry, but I am not fully understanding what you are trying to do, or rather what your problem is.  I gather that postfix is delivering mail, but to the wrong place?  Postfix will deliver according to the setting for mydestination.  According to your setup, you appear to have a set of hash tables that define the mapping from the virtual hosts to the mailbox/maildir location.  It sounds like you need to look into how these are set up.

yes I wanna change the place of deliver messages, all the settings from the fetchmail are correct, it retrieve the mails from an external host and deliver them into the postfix to the proper account, but it place the messages into /var/mail/useraccount although in the main.cf I changed the path to be in /var/mail/vhosts/domain.com/useraccount.

So how I can do that?

---

### Post by snake_eyes on 2009-12-28
where are you experts :(

---

### Post by noway2 on 2009-12-28
Ok, lets go through the configuration.  Maybe we will see something, or at least give you an idea as to where to look.

1) virtual_mailbox_base = domain.com.  This configures a virtual domain called domain.com, which means that mail for this domain will be handled by the virtual agent, not the local agent.

2) virtual_mailbox_base: This sets the directory base that will be used for the virtual domains.  In this case it is /var/mail/vhosts, so mail should go to /var/mail/vhosts/domain.com/....

3) You now must use virtual_mailbox_maps to map the email addresses to their mailbox files, which it looks like you've done.  Note: Every user receiving mail to a virtual mailbox file must have an entry in a Postfix lookup table. The mailbox file is specified relative to irtual_mailbox_base.

4) You appear to have setup the UID and GID maps, to use the same static id.  This appears correct to me.

5) check what it is in the virtual alias maps.  These messages will get FORWARDED elsewhere rather than being locally delivered.

Ok, so as far as I can tell, it looks like you have things properly configured.  This leaves me with two thoughts.  1 - did you run postmap on the hash tables, and 2 - did you restart postfix after making changes?

---

### Post by snake_eyes on 2009-12-28
Thank you for your reply,

for sure i ran postmap /etc/postfix/virtual and postmap /etc/postfix/vmailbox then /etc/init.d/postfix reload.

the problem now is why it deliver the mail that comes from the fetchmail to the default path which is /var/mail/useraccount instead of the /var/mail/vhosts/domain.com/useraccount as per my configuration, anyway here is my /etc/postfix/virtual:
> 
[email]admin@domain.com[/email]	admin


and here is my /etc/postfix/vmailbox:
> 
[email]admin@domain.com[/email]		domain.com/admin/
@domain.com		domain.com/catchall/


so where I'm wroing?

---

### Post by noway2 on 2009-12-28
Not sure as it looks like the correct syntax.  I am wondering if the problem isn't in main.cf, but rather in master.cf in as much as the wrong delivery agent is being activated(??).  The master.cf file is pretty cryptic to me still, but it is what activates the daemon programs that do the work on various conditions.  The next thing I would do is turn on the debugging in both Postfix and Dovecot.  You will need to look through the config files, but I think there are 3 places you set debug to yes on total.  Then look through the logs very carefully as these will tell you what maps files are being used and what postfix is validating against, etc, and hopefully where it is getting the wrong locations from.

If all that fails, and you wind up stumped, it may be easier to go around the problem.  On my server, I use a mysql database instead of hash files.  It is fairly easy to setup and manage through the use of the PHP package postfixadmin, if you run a web server too.  In the process of setting that up you may 'inadvertently' correct or remove whatever is going wrong.

---

### Post by snake_eyes on 2009-12-29
thank you for your information, let's start from scratch step by step how to install the fetchmail and postfix with mysql database instead plus the postfixadmin, although here is my master.cf too:

Waiting your kind reply please...

> 
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
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
proxywrite unix -       -       n       -       1       proxymap
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
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
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
  ${nexthop} ${user}



---

### Post by noway2 on 2009-12-29
I tried comparing your master.cf file with mine.  The only difference that I can see that might explain what is happening is that I have the following line (I use Dovecot as my delivery agent): 
dovecot unix - n n - - pipe flags=DRhu user=vmail:mail argv=/usr/lib/dovecot/deliver -d $(recipient)

What caught my attention is that it makes use of the virtual user and group ID accounts.

Before you go the re-install route, be sure to turn on debugging and look in the logs.  If you do go that way, as far as email guides, I personally like this one the best: [http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/](http://johnny.chadda.se/2007/04/15/mail-server-howto-postfix-and-dovecot-with-mysql-and-tlsssl-postgrey-and-dspam/)

*** BE VERY CAREFUL when creating the mysql configuration files. **** The text and blog editors, such as wordpress, frequently confuse the ' (single quote) and the ` (back tick).  Getting the wrong one will result in syntax errors (look in the logs).

---

### Post by snake_eyes on 2009-12-29
thank you for you advice, I will review the document today, but I wanna ask, did you install it and are you using the postfix and mysql as a server, same what I'm looking for? if yes is it stable and what is the disintegrative with this?

---

### Post by noway2 on 2009-12-29
Yes, I am using postfix with dovecot and mysql (virtual mailboxes).  I have been running my own email system for almost a year now.  I had a lot of problems getting it up and running the way I wanted it and spent a solid month of weekends working on it. At the same time, I was still a newbie to Ubuntu, though.  If I recall, I copied a lot of the information from the link I sent earlier (and have comments about it in my main.cf).  However, I may have also borrowed from other ones such as the one on howtoforge.  Note, I am sending you a PM with some information on these links.  

One BIG, and I mean BIG piece of advice I can give you is back up the configuration files for everything that you have working.  For example, backup master.cf, main.cf dovecot.conf, etc and make a safe copy of them.  That way if you screw up, you can easily go back to where you were with your working copy.  You will undoubtedly run into a problems before you get it working the way you want.

I am really not sure where you are running into problems and I was hoping some of the other experts might.

---

