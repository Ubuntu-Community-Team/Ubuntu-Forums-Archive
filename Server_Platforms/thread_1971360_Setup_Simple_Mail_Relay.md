---
title: "Setup Simple Mail Relay"
date: 2012-05-02
forum: Server Platforms
---

### Post by badman3k on 2012-05-02
Hi All!

I'm trying to find some information on setting up a simple mail relay server using Ubuntu.

We have a multi-function printer at our offices that doesn't support TLS/SSL and unfortunately we've just moved providers and they require at least SSL.

The costs of upgrading the printer to support SSL as just far too much and after some reading believe that a simple Mail relay server would suffice.

What I'm hoping is that someone could point me in the direction of a tutorial on how to set up a mail server that will accept incoming messages from this one device, and retransmit them to our mail provider using the SSL encryption.

I've read a number of tutorials on setting mail servers but a lot of them focus on setting them up as actual mail servers, not relays.

Any help/pointers/tutorials would be most helpful.

Many thanks in advance,
Richard.

---

### Post by SeijiSensei on 2012-05-02
While Postfix is the default MTA for Ubuntu, I think sendmail is a better solution for a simple mail relay.

First, install a copy of Ubuntu server on some clunker machine in your office.  It doesn't need much horsepower at all; even a 486 with 256 MB of RAM would suffice.  Now we're going to replace Postfix with sendmail:

```

sudo apt-get purge postfix
sudo apt-get install sendmail

```

Next go to the /etc/mail directory and edit (as root with sudo) the file sendmail.cf.  You need to change three lines in that file.  First, find the line that begins with "DS" and add the name of the relay host immediately thereafter:

```

# "Smart" relay host (may be null)
DSyour.mail.provider.com

```

Note that there's no space between "DS" and the hostname.

Next, you'll need to remove the limitation that sendmail listens only to the localhost interface.  Find the two lines that read:

```

O DaemonPortOptions=Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1
O DaemonPortOptions=Family=inet,  Name=MSP-v4, Port=submission, M=Ea, Addr=127.0.0.1
```

and delete the "[font=courier], Addr=127.0.0.1[/font]" from the end of each line.  Sendmail will then listen on all interfaces.

Now restart sendmail with "sudo service sendmail restart".

The only remaining issue is how to route mail to this box for relaying.  I take it you don't want all the mail to go through here, just the messages you described.  (I'm not really clear how this relates to the printer, but we'll leave that up to you.)  Give the box a hostname like "relay.yourdomain.com" and add an A record entry to your internal DNS for it.

Let's do a bit of testing before moving on.  Run "telnet relay.yourdomain.com 25" and you should be the sendmail banner in reply.  Let's suppose that you're sendmail a message From [email]testing@yourdomain.com[/email] to [email]printer@relayhost.com[/email].  Follow these steps to test your configuration.  The entries you type are in bold:

```

$ **telnet relay.yourdomain.com 25**
[stuff]
220 relay.yourdomain.com ESMTP Sendmail 8.14.4/8.14.4/Debian-2ubuntu2; Wed, 2 May 2012 1ing access from: localhost(OK)-localhost [127.0.0.1]
**ehlo hostname.of.sending.machine**
250-relay.yourdomain.com Hello hostname.of.sending.machine [ip.of.sending.machine], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
**mail from:testing@yourdomain.com**
250 2.1.0 testing@yourdomain.com... Sender ok
**rcpt to:printer@relayhost.com**
250 2.1.5 printer@relayhost.com... Recipient ok
**data**
354 Enter mail, end with "." on a line by itself
[B]testing testing testing
.[/B]
250 2.0.0 q42JroEC005697 Message accepted for delivery
**quit**
221 2.0.0 relay.yourdomain.com closing connection

```

We're almost done, but I need to know a bit more about how mail is configured within your office.  Do you have an existing mail server?  Can it be configured to route mail by domains?  If so, tell it to send mail for the offsite provider that requires SSL to the relay box and handle all other mail the way it does now.  If you can't get this configured properly, ask me again, and we'll set up the relay box to handle routing.

---

### Post by badman3k on 2012-05-03
@SeijiSensei: many thanks for getting back to me with such a detailed response; I really appreciate it.

I've not had chance to implement it as of yet, but will give it a try later on and see where I get to.

In response to your questions:

[LIST]
[*]The printer needs an SMTP server address, login and password to send the email; these are manually entered into the printer settings.

[*]There is no internal mail server on the network. Our mail server is in the cloud. In essence the printer makes a connection using the settings above to connect to the relay server which in turn relays the message to the cloud based server for "processing"
[/LIST]

I hope this answers your questions, but if not, just let me know and I'll try and provide some more information.

Many thanks again, and I'll let you know how I get on with the instructions you've provided already.

-Richard

---

### Post by Jonathan L on 2012-05-03
Hi badman

> While Postfix is the default MTA for Ubuntu, I think sendmail is a better solution for a simple mail relay.Seiji advice is impeccible as ever.  Even though I've mostly used sendmail, with great success over the years, it has to be said the maintenance of the configuration can be tricky.  Here's the alternative with postfix, if you wanted to try that too.

I tested it by telnet at Amazon Web Services, relaying through Google's gmail servers to an account at Yahoo.  For your application, I'd use an old box in the corner, Ubuntu 10.04.4 LTS server.

Get the software:
```
apt-get install -y postfix

```You'll get a choice: use "Satellite"

[LIST]
[*]Choose any sensible hostname, perhaps "printerfriend.example.com"
[*]Choose your external "real" email gateway, perhaps "smtp.myisp.com"
[/LIST]

Then edit /etc/postfix/main.cf, here in full, with my edits in red.

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
[COLOR=Red]smtp_tls_security_level = encrypt[/COLOR]

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = [COLOR=Red]ec2-46-137-57-105.eu-west-1.compute.amazonaws.com[/COLOR]
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = [COLOR=Red]ec2-46-137-57-105.eu-west-1.compute.amazonaws.com[/COLOR], localhost
[COLOR=Red]relayhost = [smtp.gmail.com]
smtp_sasl_auth_enable = yes  
smtp_sasl_password_maps = hash:/etc/postfix/relay_passwd  
smtp_sasl_security_options =[/COLOR]
[COLOR=Red]#[/COLOR]mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
[COLOR=Red]mynetworks_style = subnet[/COLOR]
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = [COLOR=Red]all[/COLOR]
```Put a password in the relay_passwd file:

```
smtp.gmail.com username@gmail.com:plaintextpassword
```Cook the map and restart:
```
sudo postmap /etc/postfix/relay_passwd
sudo /etc/init.d/postfix restart
```Test just like Seiji says.  You might care for a fuller message to check the from and to addresses show up
```
...
data
From: Mr Printer <printer@example.com>
To: Whoever <whatever@yousaid.com>
Subject: Scan 1234

Hello
.
```Hope that helps.

Kind regards,
Jonathan.

---

### Post by SeijiSensei on 2012-05-03
> **badman3k said:**
> The printer needs an SMTP server address, login and password to send the email; these are manually entered into the printer settings.

Then give the printer the relay box as its SMTP server.  I would think the login information is optional, no?  It's possible to set up an SMTP server that requires a login, but it's not mandatory.  The solution I suggested doesn't require a login.

Why isn't it possible simply to point the printer to your current off-site SMTP server?

---

