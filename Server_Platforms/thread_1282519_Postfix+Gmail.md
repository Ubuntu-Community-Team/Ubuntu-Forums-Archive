---
title: "Postfix+Gmail"
date: 2009-10-04
forum: Server Platforms
---

### Post by januzi on 2009-10-04
Hi

I moved my website to the new server and there are problems with postfix and gmail. 
At the old server there was:
> 
to=<biuro@tuszmarkt.pl>, relay=aspmx.l.google.com[209.85.219.3]:25, delay=0.62, delays=0/0/0.09/0.52, dsn=2.0.0, status=sent (250 2.0.0 OK 1245829703 3si1578239ewy.63)
and now there is:
> 
to=<biuro@tuszmarkt.pl>, relay=none, delay=0.06, delays=0.06/0/0/0, dsn=5.4.6, status=bounced (mail for tuszmarkt.pl loops back to myself)
As I remember I set only mx on the old server (no .forward, transport, etc) and it was all I have to do. 

Did I miss something ? Or maybe I set something wrong in the local bind server ?

postconf -n
> 
command_directory = /usr/sbin
config_directory = /etc/postfix
daemon_directory = /usr/lib/postfix
data_directory = /var/lib/postfix
debug_peer_level = 2
home_mailbox = .maildir/
html_directory = /usr/share/doc/postfix-2.5.7/html
inet_interfaces = all
mail_owner = postfix
mailq_path = /usr/bin/mailq
manpage_directory = /usr/share/man
mydestination =
mydomain = tuszmarkt.pl
myhostname = tuszmarkt.pl
newaliases_path = /usr/bin/newaliases
queue_directory = /var/spool/postfix
readme_directory = /usr/share/doc/postfix-2.5.7/readme
receive_override_options = no_unknown_recipient_checks,no_address_mappings,no_header_body_checks
sample_directory = /etc/postfix
sendmail_path = /usr/sbin/sendmail
setgid_group = postdrop
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/saslpass
smtp_sasl_security_options =
smtpd_recipient_restrictions = permit_sasl_authenticated,reject_unauth_destination
smtpd_sasl_path = smtpd
unknown_local_recipient_reject_code = 550
tuszmarkt.pl.hosts (part)
> 
tuszmarkt.pl.           IN      MX      10 aspmx.l.google.com.
tuszmarkt.pl.   IN      TXT     "v=spf1 a ptr a:tuszmarkt.pl mx:tuszmarkt.pl mx:aspmx.l.google.com ip4:194.169.126.23 ip4:194.169.126.24 ip4:194.169.126.25 ip4:194.169.126.26 ip4:194.169.126.27 include:aspmx.googlemail.com ~all"



Edit2:
I added relayhost to the main.cf: 
> 
relayhost = [aspmx.l.google.com]:25

Now, emails are going out to the gmail, but I'm not sure if this is a good solution. And I still don't know why postfix doesn't want to use mx record from the bind.

---

