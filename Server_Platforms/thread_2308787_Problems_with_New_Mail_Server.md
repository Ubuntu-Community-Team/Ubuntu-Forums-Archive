---
title: "Problems with New Mail Server"
date: 2016-01-05
forum: Server Platforms
---

### Post by Clockmender on 2016-01-05
Hello Wise Sages

I am not sure if I have put this in the correct place, so please forgive me if not. I have built a new LAMP server for my flying club. Everything goes well, Apache2 is fine, Wordpress is fine, etc, I can send mail from the accounts in the mail system, but I always get:

relay=mailman, delay=0.13, delays=0.04/0/0/0.09, dsn=5.1.1, status=bounced (user unknown)

When I send from one local mail to another, I can send mail to outside accounts, like my iCloud account. When I send mail to my mail server accounts I get:
```

Action: failed
Status: 5.1.1
Diagnostic-Code: x-unix; user unknown
```

I am now at a loss, since the email addresses I am sending to are in the "mailserver" database "virtual_users" table as viewed from phpmyadmin.

Can anyone point me in the right direction, I have not posted all the output here, I will wait for some kind sole to say "Post this file" first.

but this might help from postconf -n (Actual domain name redacted to MYDOMAIN)
```

[email]root@server1:/var/vmail/MYDOMAIN.co.uk[/email]/mailman/Maildir# postconf -n

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
content_filter = smtp-amavis:[127.0.0.1]:10024
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
local_transport = lmtp:unix:private/dovecot-lmtp
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mailman_destination_recipient_limit = 1
mydestination = $myhostname, $mydomain, localhost.$mydomain, localhost
mydomain = MYDOMAIN.co.uk
myhostname = MYDOMAIN
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relay_domains = MYDOMAIN.co.uk
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
smtpd_tls_cert_file = /etc/letsencrypt/live/MYDOMAIN.co.uk/cert.pem
smtpd_tls_key_file = /etc/letsencrypt/live/MYDOMAIN.co.uk/privkey.pem
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
transport_maps = hash:/etc/postfix/transport
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_transport = lmtp:unix:private/dovecot-lmtp
```

Let me know if you can help or if you need more info. Also I have forgotten how to post code properly........

Thanks Mr Moderator!

This may help in that it is the code used to query the database:

```

mysql> SELECT email as user, password FROM virtual_users WHERE email='bgc-it@MYDOMAIN.co.uk';
+------------------------+-------------------------------------------------------------------------------+
| user                   | password                                                                      |
+------------------------+-------------------------------------------------------------------------------+
| bgc-it@MYDOMAIN.co.uk | {SHA256-CRYPT}$5$zOVfhqdH4, blah blah blah, ASLO REDACTED!!!!!
+------------------------+-------------------------------------------------------------------------------+
1 row in set (0.00 sec)

```

The query is stored in the /etc/dovecot/dovecot-sql.conf.ext config file telling Dovecot how to query usernames. The query expression contains '%u' not an actual value, but I tried the expression from the config file with a real value just to see if it works or not.

Thanks, Clock.:D

---

### Post by lisati on 2016-01-05
*Thread moved to **Server Platforms**.*

---

### Post by Clockmender on 2016-01-07
No clues then....

Could this be  mailman problem?

I am STILL getting this:

```

Jan  7 21:56:29 server1 postfix/qmgr[7361]: 002903480D8C: removed
Jan  7 21:56:30 server1 dovecot: imap-login: Login: user=<ME@MYDOMAIN.co.uk>, method=PLAIN, rip=::1, lip=::1, mpid=7933, secured, session=<NboPi8UodwAAAAAAAAAAAAAAAAAAAAAB>
Jan  7 21:56:29 server1 postfix/pipe[7927]: 002903480D8C: to=<ME@MYDOMAIN.co.uk>, relay=mailman, delay=0.14, delays=0.04/0/0/0.1, dsn=5.1.1, status=bounced (user unknown)
Jan  7 21:56:29 server1 postfix/qmgr[7361]: 002903480D8C: removed

```

So why is the user recognised as a login, then the mail bounced, can someone help please?

Cheers, Clock.

---

### Post by Clockmender on 2016-01-10
So - Does nobody know the answer to this?
Or - Does nobody want to help me?
Or - Do you all think I can work this out for myself?
Or - Did I not ask nicely enough?

Hmm - not so good I think.....

---

### Post by SeijiSensei on 2016-01-10
Your question requires someone who knows a lot about Postfix and something about mailman it appears.  As a long-time sendmail user, I can't help with Postfix.  I have gotten mailman up and running on a test-bed machine with sendmail as the SMTP exchanger. I also avoid complications like virtual domains and users and just assign mail recipients ordinary accounts on the Linux box.  You have just about every complexity possible in that configuration including SASL, TLS, transport maps, and a MySQL back end.

I'd start by trying to figure out what "relay=mailman" is supposed to mean.  It looks like the server thinks mail for mydomain.co.uk needs to be relayed to another host rather than delivered locally, but again I'm no Postfix expert.

---

### Post by Clockmender on 2016-01-11
Thanks for that: Relay=mailman is from the Mailman setup, where the tutorials said to edit the transport file so the domain is routed to mailman. Interestingly some other tutorials and help pages (Including Ubuntu Wiki in places, but not consistently) says to set the transport to "local" then relay would read relay=local. The server can send out email through Roundcube and Squirrelmail, even to groups with no problems. It's just when mail is sent into the server, senders always get Diagnostic-Code: x-unix; user unknown. I do not know what to do next as there seem to be so many conflicting pieces of advice out there, none of which has solved the issue. It has been suggested the I have not setup DNS correctly, but the bringer of that news did not add anything about how DNS should be set up for a mail/web/owncloud server!

Cheers, Clock.

---

### Post by SeijiSensei on 2016-01-11
Setting up DNS "correctly" requires only that the primary MX record for mydomain.co.uk points to your server.  From the looks of things, that's not the problem.  You also have "mydestination" set to include the domain, so Postfix should know it is the final delivery server.  I believe "transport_maps" overrides these things though, much like a sendmail mailertable.  What if you comment out the transport_maps directive?

I assume the account referenced as [email]ME@mydomain.co.uk[/email] exists in the MySQL database, right?

---

### Post by darkod on 2016-01-11
You should also post the content of mysql-virtual-mailbox-maps.cf so people can take a look. Right now the user unknown error might be related to that.

Also, pardon my ignorance, but you have postfix and dovecot. In such case isn't mailman redundant? I have seen few mail serves with only postfix and dovecot so I know it works.

Without having more data and without being an expert myself, I would say the mapping is where it fails. Double check that. And see whether you need mailman at all... I don't understand its role when postfix and dovecot are there but that might be my lack of detailed knowledge of linux mail servers.

---

### Post by Clockmender on 2016-01-11
Thank you guys, I have now removed mailman and set the virtual_transport to dovecot. I also junked and re-wrote my postfix main.cf and master.cf files according to this tutorial (having been pointed there by a kind soul with more knowledge than me!):

[https://www.exratione.com/2014/05/a-mailserver-on-ubuntu-1404-postfix-dovecot-mysql/](https://www.exratione.com/2014/05/a-mailserver-on-ubuntu-1404-postfix-dovecot-mysql/)

I then altered the dovecot-sql.con.ext file to use the correct vmail id's (Oh boy did that one take some finding in the web help files......) and restarted postfix and dovecot and all of a sudden I could send mail from one local address to another! I can also send mail into the server, but I get greylist warnings in the mail.log file, so I will investigate that and see if I can solve that one next.

I also checked all my mysql_*.cf files for errors and there were none, much to my surprise, but that only served to make me look elsewhere for errors.

Thanks for the pointers. I am not going to post my old files as they appear to be totally FUBAR, much to my embarrassment....

Thank you all again, Clock.

---

### Post by SeijiSensei on 2016-01-11
Mailman is a listserver program like majordomo.  It handles deliveries to mailing lists with tools to manage subscriptions and the like.  I was assuming that Clock was supporting a listserver.  Mailman is totally unnecessary for a server that simply accepts mail and delivers it to local mailboxes or forwards it on to relay hosts.

---

### Post by Clockmender on 2016-01-12
Thanks again SeijiSensei - I thought I had to install mailman to handle bulk mail shots from my Gliding Club (This is who the server is for) to its membership. I found that a far easier way was to create groups of contacts in Roundcube and merely BCC the emails to the group. In this scenario you don't need a "To" address and the recipients see the "Address To" field as "Unknown Recipients", which is what I want. My initial thought was to mimic our club's old system whereby you send a mail to the [email]mailer@MYDOMAIN.co.uk[/email] address and this is then sent out to all the other contacts using something like Mailman. This has proven to be cumbersome and my revised scheme works much easier for those in the club who are authorised to send mail shots. They just logon to Roundcube, select the group as the BCC addresses, write the email and click Send. The old system was good for more experienced IT users, but not the club's chairman!

The error I believe was somewhere in the main.cf and master.cf Postfix config files - maybe I will never know! I just rebuilt them from scratch and it worked. I think it is a problem with internet tutorials where often some vital piece of information is missing and the writer assumes you know that piece of information and have already done the necessary steps. The tutorial I referenced above seems to cover everything, Assuming you have set DNS A, and MX records with your domain registrar and opened all the required ports on your router - maybe the writer should also point this out in his tutorial.... All that I had done, I had also tested the mysql maps using *postconf -q* to make sure they where working.

I have Postgrey installed as well, I found that once I had added the "Reply To" address and domain to the whitelists, mails back to the server came through straight away, rather than being held for an hour. I noticed that icloud.com was not in the whitelist, but amazon.com was - curious.

This is the first mail server I have ever built by the way, so I expected some teething trouble, the website and owncloud installs, including Wordpress went very smoothly, including setting up ftp for uploads. I can recommend owncloud for this type of application where the club's data can be made available to all members through their browsers.

Other system setup parameters - 64bit processor 8Gb ram, 1.5Tb of disc, Ubuntu Server 14.04 OS, SSL certificates from Letsencrypt (fully supported/verified and at no cost), SSH for remote mods from my Mac, rather than using the console screen on the server, I use iTerm on the Mac. Server has it own UPS with Wake-Up-On-LAN. Apache2 is used for web hosting, with phpmyadmin and postfixadmin also installed.

Thanks again for the help, Clock.

---

