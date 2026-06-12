---
title: "how to allow wordpress to send email from server"
date: 2008-07-30
forum: Server Platforms
---

### Post by cocotu on 2008-07-30
we have a development server.  we are working with wordpress.  as you know when you install wordpress at one of the many hosting companies wordpress is able to send confirmation emails.  how can i do this with our dev linux box? i already installed postfix, is this enough for wordpress? thanks...

---

### Post by sterilegenie on 2008-07-30
I too am running wordpress and i have no problems with emails being sent. Have you configured WP correctly?

---

### Post by jdavis on 2008-07-31
Try the following:

```
sudo apt-get install sendmail
```

I think that should allow PHP applications to send email.

---

### Post by windependence on 2008-07-31
Actually postfix is a drop in replacement (and better) than sendmail. No need to install sendmail, in fact he will probably mess up postfix if he does that.

What is in your /etc/postfix/main.cf
file?

Also have you restarted postfix? 

```
sudo /etc/init.d/postfix restart
```

-Tim

---

### Post by cocotu on 2008-07-31
thanks guys! this is my main.cf: (should i change anything?)

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

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = blaster.bhvr.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = blaster.bhvr.net, localhost.bhvr.net, , localhost
relayhost = smtp.emailsrvr.com
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/

---

### Post by cocotu on 2008-07-31
sendmail is installed in this box, should i remove it? thanks.

---

### Post by theolster on 2008-07-31
I've also being having the same problem (I think).  PHP needs to be configured to handle either Sendmail/Postfix/Exim/etc.  I think I've got the hang of the php.ini side of things, I just can't correctly configure the Sendmail.

Any posible solution for this would be greatfully recieved.

[(The thread I started is here)]("http://ubuntuforums.org/showthread.php?p=5482273")

---

### Post by cocotu on 2008-07-31
trying to follow:
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

the part that says 'Test your default setup'
i'm not able to see any messages when i type the 'mail' command- "No mail for fmaster". i'm able to see the mail at the Maildir directory. this is a development server and its accessible in our LAN only and is for test purposes only. is there anything else i'm missing? thanks..

---

### Post by windependence on 2008-08-01
> **cocotu said:**
> sendmail is installed in this box, should i remove it? thanks.

No, you definitely don't want to uninstall sendmail. Just install postfix and set your hostname and domain. Postfix needs little configuration to use the php mail() function.

-Tim

---

### Post by windependence on 2008-08-01
> **theolster said:**
> I've also being having the same problem (I think).  PHP needs to be configured to handle either Sendmail/Postfix/Exim/etc.  I think I've got the hang of the php.ini side of things, I just can't correctly configure the Sendmail.

Any posible solution for this would be greatfully recieved.

[(The thread I started is here)]("http://ubuntuforums.org/showthread.php?p=5482273")

You don't need to do anything to php tp make it work with either sendmail or postfix.

-Tim

---

### Post by cocotu on 2008-08-01
i'm running this inside our LAN.  can i configure it to use an external SMTP server? i found a wordpress plugin and not sure if it works, but wanted to know how to do this from server.  do we need a domain name for this? and point the MX records to this development server? i'm a little confused...thanks

---

### Post by windependence on 2008-08-01
Yes you can but it's not necessary and won't look professional not coming from your domain, it will appear to come from the smtp domain. OK if you don't mind but honestly, getting postfix to work should be a 10 minute thing.

-Tim

---

### Post by cocotu on 2008-08-01
the plugin works and it sends the email from the default wordpress installation.  using postfix do i need to point the MX records from our domain to the development box in order for this to work? thanks...

---

### Post by windependence on 2008-08-01
Nope, not if you're only sending mail.

-Tim

---

### Post by cocotu on 2008-08-01
thanks win, but i seem kind of lost. i configured postfix and still no luck.  i know google is my 'FRIEND' but can't seem to figure this out. i will keep trying with your friend google. thanks

---

### Post by OliverHaslam on 2012-06-02
Dragging an old thread back up, I know, but I've got the same question so thought it was better than starting another.
 
I've got Wordpress installed on my Ubuntu web server and want it to be able to send emails for comments and the like. At the moment, it can't.
 
I get the usual error:
>  
Possible reason: your host may have disabled the mail() function

 
I use msmtp to send emails for a crontjob that I have set up - can I use this and tell WP to use it, or should I dump msmtp completely and use something else?
 
Cheers.

---

### Post by j0hnx777 on 2012-09-06
I am also trying to allow PHPMail through my server. My php mailer script has the host and port settings configured, but for some reason I can't get mail out from my server. I just installed postfix, but I'm not really sure where to go from there.

---

