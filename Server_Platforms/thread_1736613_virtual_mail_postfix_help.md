---
title: "virtual mail postfix help"
date: 2011-04-22
forum: Server Platforms
---

### Post by wsonar on 2011-04-22
I have followed this and setup virtual domains for email

[https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto]("https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto")

I now have apache hosting virtual domains and postfix and mysql setup for virtual mail


I'm a little confused on handling the mx records for virtual domains

is there a way to point the mail records to mail.domain1.net and mail.domain2.com
if the server is somethingelse.domain1.net

should I make my local box on a more generic local domain from the ones I am hosting

any help and advice greatly appreciated I want to make sure everything is right so I not mistaken for spam

ultimate goal to use php mail functions from the different domains on the server

---

### Post by wsonar on 2011-04-22
Never mind I think i was retarded I can just set up pointers to point it where i want

---

### Post by wsonar on 2011-04-22
Still don't have the virtual mail working

I setup users and mailboxes in the postfix.admin

but am not sure how to authinicate to them

---

### Post by elico on 2011-04-22
i'm recommending on this nice tutorial:
[http://workaround.org/ispmail/lenny](http://workaround.org/ispmail/lenny)
it's missing a line on the main.cf file:
> virtual_mailbox_base = /var/vmail
else then this the manual is good and is much more then the one used on ubuntu that you have used.
one of my server is running using this manual.
im writing a big one myself (cross distribution) but it will take some time.

---

### Post by wsonar on 2011-04-22
would this affect anything?

```

Apr 22 18:13:39 authdaemond: modules="authmysql", daemons=5
Apr 22 18:13:39 authdaemond: Installing libauthmysql
Apr 22 18:13:39 authdaemond: file not found

```

---

### Post by wsonar on 2011-04-22
forgot to install this modual

courier-authlib-mysql

---

### Post by wsonar on 2011-04-22
Works now

:)

---

### Post by wsonar on 2011-04-22
my certificates are generic will gmail and others mark me as spam?

what is the best way to create them for each virtual domain?

---

### Post by wsonar on 2011-04-22
still not totally right damn mail is such a pain

---

### Post by wsonar on 2011-04-22
SASL authentication failure: Password verification failed

---

### Post by wsonar on 2011-04-22
When I try to send to my acount from my yahoo I get

NOQUEUE: reject: RCPT from nm25-vm0.bullet.mail.sp2.yahoo.com[98.139.91.228]: 451 4.3.5 Server configuration problem;


warning: connect to 127.0.0.1:10023: Connection refused

---

### Post by bmathis on 2011-04-22
Can you post your main.cf file contents

---

### Post by wsonar on 2011-04-23
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

readme_directory = /usr/share/doc/postfix

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
mydestination =
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html

# Virtual Mailbox Domain Settings

virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_mailbox_limit = 51200000
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_transport = virtual


# Additional for quota support

virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql_virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = Sorry, the your maildir has overdrawn your diskspace quota, please free up some of spaces of your mailbox try again.
virtual_overquota_bounce = yes

smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unknown_recipient_doma$
# modify the existing smtpd_sender_restrictions
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
# then add these
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =


```

---

### Post by wsonar on 2011-04-23
I opened the secure port on my firewall and can now receive from external sources

I just need to figure out the send now

---

### Post by wsonar on 2011-04-23
I have 465 allow in ufw but I cannot telnet to it from the localhost

---

### Post by wsonar on 2011-04-23
I can send through telnet 25

but I can't send from an authenticated account

---

### Post by wsonar on 2011-04-23
I don't seem to be able to telnet to  ports 10023 or 10024

either

---

### Post by wsonar on 2011-04-23
not I can't receive from outside again not sure if it has something to do with the amavis

I get this

warning: problem talking to server 127.0.0.1:10023: Connection refused

---

### Post by wsonar on 2011-04-23
no matter what type I choose I get this

warning: SASL authentication failure:

---

### Post by wsonar on 2011-04-23
Cannot send or receive now



real frustrating

---

### Post by wsonar on 2011-04-23
getting closer think it has to do with postgrey

---

### Post by wsonar on 2011-04-23
I removed this
smtpd_recipient_restrictions = 
inet:127.0.0.1:10023 

I can recive from outside now

---

### Post by wsonar on 2011-04-23
still get this no matter what ype I try

warning: SASL authentication failure: Password verification failed

---

### Post by wsonar on 2011-04-23
I commented out all of this and I can send now no problem

#smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, #reject_non_fqdn_sender, reject_unknown_sender_domain, #reject_unauth_pipelining, permit
# then add these
#smtpd_sasl_auth_enable = yes
#broken_sasl_auth_clients = yes
#smtpd_sasl_security_options = noanonymous
#smtpd_sasl_local_domain =



anybody know what I can do to fix this?

---

### Post by wsonar on 2011-04-23
I get an access denied if I try to email to my gmail

Relay access denied;

---

### Post by wsonar on 2011-04-23
I can send external from telnet but not from a client

---

### Post by wsonar on 2011-04-23
found another problem 
mynetworks = 127.0.0.1
was instead of
mynetworks = all

---

### Post by wsonar on 2011-04-23
still cannot send external fromm a client

---

### Post by wsonar on 2011-04-23
this is killing me any help greatly appreciated

---

### Post by wsonar on 2011-04-23
cannot get sasl to work to save my life

warning: SASL authentication failure: Password verification failed

---

### Post by wsonar on 2011-04-23
This [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto]("https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto")
has pissed me off because half way through it says to use

[http://www.starbridge.org/spip/spip.php?article1&lang=fr]("http://www.starbridge.org/spip/spip.php?article1&lang=fr")

which is setup totally different

this is pissing me off


Its rediculas having to skeleton together something from three different howto's and forums why can't one just work right I had already stated one way half way through don't want tom start over another way

---

### Post by wsonar on 2011-04-23
I thought I was close I was missing libpam-mysql

after install I get the password promt but it is still not valid

---

### Post by HermanAB on 2011-04-24
Oh goodness me.  This thread is a living proof of why I quit using Postfix about 12 years ago.

You could install Citadel from the repos.  It only takes a few minutes and it does absolutely everything.  It really, truly 'Just Works (TM)'.

Citadel is nice because the default system is simple and works perfectly with zero hassle.  You can customize it later by installing a different webmail system and so on if you don't like the default.

[http://citadel.org](http://citadel.org)

---

### Post by wsonar on 2011-04-24
lol

yea I had a lot of other things I could have used this time for

---

### Post by wsonar on 2011-04-24
If I don't continue the current path and get it to work the my time would have been wasted so I have to make this work will look at citadel for the future

---

### Post by HermanAB on 2011-04-24
Postfix sure is a good way to learn how mail transports work, but you probably need to throw your howto guides away and go to the Postfix project web site instead:
[http://www.postfix.org/](http://www.postfix.org/)

All you need to know is explained there.

---

### Post by wsonar on 2011-04-24
I've had one domain with postfix and dovecot but multiple is more tricky almost considering just keeping them on separate boxes


I don't understand why sasl don't like the password it's getting it from mysql and it's the same as the one for reciving and I can recieve

I need a way to test to see what password sasl is using


When I create the user in postfixadmin it puts the password in mysql in a hash format

how does the smtp agent convert it from the hased password to the correct type (plain login cram-md5 digest-md5)

---

### Post by wsonar on 2011-04-24
Well sasl works now but only with normal password not encrypted

---

### Post by wsonar on 2011-04-24
It's a miracle I just sent using thunderbird from both of my domains to my gmail and it arived in my gmail inbox

---

### Post by wsonar on 2011-04-24
edited

---

### Post by wsonar on 2011-04-25
I can send fine now from clients to internal and external and I can send from php scrip to internal but when I try php script to external 

it's sending from:www-data instead of who I specify

---

### Post by wsonar on 2011-04-25
my server puts from=<www-data@computername.mydomain.com> //which is not where my mail pointers point
it's in the /var/log/mail.log

when I send it to myself the virtual domains I'm hosting on this box I get it no problem and the header information looks right

I assume it's getting rejected from gmail and yahoo because of this

recipient invalid domain (in reply to RCPT TO command))

when I send from thunderbird the mail.log  show's sent from correct virtual server
but when I send from php it puts from=<www-data@computername.mydomain.com>

---

### Post by wsonar on 2011-04-25
a php issue from here

---

