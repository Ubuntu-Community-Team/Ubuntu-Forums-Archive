---
title: "Strange postfix problems"
date: 2007-06-21
forum: Server Platforms
---

### Post by XAsmodeanX on 2007-06-21
Hey guys, 
     I followed the mail guide on the wiki to set up postfix/dovecot and all that stuff.  I can send mail out and receive mail from any address when using squirrelmail or outlook.  However, when using my smartphone, I can get mail but cannot send mail out.  The error is this from /var/log/mail.log:

Jun 21 08:41:20 pegasus postfix/smtpd[22594]: warning: 166.205.104.72: hostname 166-205-104-072.mobile.mymmode.com verification failed: No address associated with hostname


Any ideas how to fix that?  I need to be able to send/receive from the mobile phone like everything else that works.

---

### Post by Widodh on 2007-06-21
This is because there is no "A" record in the DNS for "166-205-104-072.mobile.mymmode.com"

root@server:~# host 166-205-104-072.mobile.mymmode.com
166-205-104-072.mobile.mymmode.com does not exist, try again
root@server:~#

That's you problem.

I think you have some smtpd or sender restrictions in your main.cf about hostnames which should be resolved.

---

### Post by XAsmodeanX on 2007-06-21
Could you point out the problem in the config file for me?  I'm not sure what to change... this is my first postfix server :)

xasmodeanx@pegasus:~$ cat /etc/postfix/main.cf 
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

#myhostname = mail.barnettesl.com
myhostname = barnettesl.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = barnettesl.com, mail.barnettesl.com, localhost.barnettesl.com, localhost
relayhost =
mynetworks = 127.0.0.0/8
home_mailbox = Maildir/
#mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated, permit_mynetworks, reject
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
local_recipient_maps = unix:passwd.byname $alias_maps

---

### Post by MJN on 2007-06-22
I think you could be well be barking up the wrong tree here. The 'warning' line you quote was just that - a warning - and indeed quite a common one. It's basically saying that when a reverse lookup was done on the connecting IP address it could not find a forward record for the result. This mismatch is being pointed out to you in case you are subsquently relying on the validity of the hostname for access control etc.
 
Post more of your logs that show what happens when you try and send a message then we can see what (the symptom of) the real problem is. It is likely to be down to your client (phone) not authenticating prior to attempting to send mail (a very quick test of this is to try and send a message to another local user (or yourself) with your phone as such a delivery won't require authentication).
 
Mathew

---

