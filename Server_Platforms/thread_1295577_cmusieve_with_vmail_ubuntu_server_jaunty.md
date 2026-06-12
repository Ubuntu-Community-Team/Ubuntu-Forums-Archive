---
title: "cmusieve with vmail ubuntu server jaunty"
date: 2009-10-19
forum: Server Platforms
---

### Post by jonathan morales on 2009-10-19
Hello, I have come to a bit of a roadblock right now trying to figure out where I've gone wrong with sieve (cmusieve). I'm using dovecot's deliver in postfix, have created a .doveot.sieve file under /var/mail/vmail/<domain>/<user>/, and mail is getting delivered as normal but the sieve just doesn't seem to be doing anything. I have log files under /var/log/mail.log, mail.info, dovecot.log.

Additionally, I have added squirrelmail and added managesieve to dovecot. The files created by that are not named .dovecot.sieve and actually find themselves in an alternate location (it's under /var/mail/vmail/<domain>/<user>/sieve/phpscript.sieve. 

Anyway with what I've done, nothing seems to be happening, and there's nothing in the logs to point me in the right direction. I tried to point a log file for sieve and no go.

Here is my /etc/postfix/main.cf
```

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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = ubuntuserver, localhost.localdomain, localhost
home_mailbox = Maildir/
virtual_mailbox_domains = /etc/postfix/vhosts
virtual_mailbox_base = /var/mail/vmail
virtual_mailbox_maps = hash:/etc/postfix/vmailbox
#virtual_transport = dovecot 
#dovecot_destination_recipient_limit = 1
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
#virtual_alias_maps = hash:/etc/postfix/virtual
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
#mailbox_command = procmail -a "$EXTENSION"
mailbox_command = /usr/lib/dovecot/deliver
#mailbox_command = 
mailbox_size_limit = 0
message_size_limit = 15000000
recipient_delimiter = +
inet_interfaces = all 
proxy_interfaces = 68.15.105.244

```

And here is my /etc/postfix/maser.cf
```

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
25      inet  n       -       -       -       -       smtpd
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
#dovecot delivery
dovecot   unix  -       n       n       -       -       pipe
 flags=DRhu user=vmail:vmail argv=/usr/lib/dovecot/deliver -f ${sender} -d ${recipient}


```

And here is my dovecot.conf
```
 
base_dir = /var/run/dovecot/
protocols = imap pop3 pop3s managesieve
disable_plaintext_auth = no
shutdown_clients = yes
log_path = /var/log/dovecot
info_log_path = /var/log/dovecot.info
log_timestamp = "%Y-%m-%d %H:%M:%S "
auth_debug_passwords = yes
#ssl_disable = yes
login_dir = /var/run/dovecot/login
login_chroot = yes
login_user = dovecot
login_greeting = hey hows it goin
mail_location = maildir:/var/mail/vmail/%d/%n
mmap_disable = no
valid_chroot_dirs = /var/spool/vmail
protocol imap {
  login_executable = /usr/lib/dovecot/imap-login
  mail_executable = /usr/lib/dovecot/imap
}
protocol pop3 {
  login_executable = /usr/lib/dovecot/pop3-login
  mail_executable = /usr/lib/dovecot/pop3
  pop3_uidl_format = %08Xu%08Xv
}
protocol lda {
mail_plugins = cmusieve
sieve_global_path = /var/vmail/globalsieverc
log_path = /var/log/dovecot-local-deliver.log
}
auth_executable = /usr/lib/dovecot/dovecot-auth
auth_verbose = yes
auth default {
  mechanisms = plain 
  passdb passwd-file {
    args = /etc/dovecot/passwd
  }
  userdb passwd-file {
    args = /etc/dovecot/users
  }
  user = root
}

```

Lastly, here is the simple test script I wrote for cmusieve

```


if header :contains "from" "morales" {
        redirect "angel@lasersource.net";
	keep;
    }


```

Hope someone can help...

---

### Post by jmkemp on 2010-02-23
Did you ever get this to work? I've got the exact same problem, with almost exactly the same settings in the various files that you have. Have also checked that dovecot is listening on port 2000. Spent a few days searching across various websites, primarily dovecot, these forums and countless blogs. No-one appears to have written up the answer.

---

### Post by jmkemp on 2010-03-08
OK. It works. Now I'm not exactly sure why but I think it is to do with the fact that there are two valid dovecot configuration files. 

The documentation leads you to believe that with a postfix mail server installed you only need to tailor the dovecot-postfix.conf file, which is what I did. Just as I was getting to the point of extracting a "dovecot -n" so that I could ask for help on the dovecot mailer I realised that it was pulling this from the dovecot.conf file and that this was different, specifically in setting the home directory for the virtual users. 

So I did the obvious thing, I re-named dovecot.conf and then copied dovecot-postfix.conf to replace it. With both conf file synchronised I then re-started dovecot. This is what fixed things (although I am uncertain as I then got some error messages about not being able to open a log file, but when that was fixed by removing the entry about the log file the virtual users started to use the sieve scripts). 

The only other thing to point out was that I found it best to login to managesieve to create the sieve files that way rather than sticking them in the appropriate user home directory. 

For me this is solved, but I'll let the thread originator label it up that way if it works for them.

---

