---
title: "Server email system"
date: 2013-03-13
forum: Server Platforms
---

### Post by kenmahn on 2013-03-13
Hi:

I have a server with 12.04 installed with no desktop, i.e., console mode only. I have an ISP server that uses Exim 4. I have a windows XP and a ubuntu desktop system. I am planning on using Thunderbird on both desktops using IMAP to my internal server so all mail stays on the local server since both of us need access to the same accounts.

The question is what email system do I need on my local server so it keeps all of the mail but also acts as a relay email. The email system needs to download all of the mail and relay any mail through the correct accounts. I have about 3 domains with 3 or more email accounts. The server is already running Apache and Postgresql for the inventory system. I will also need the ability to send emails using PHP through the server.

Thank you.
Ken

---

### Post by egpetrich on 2013-03-14
I have a server set up to handle my e-mail. There are four parts:

[LIST=1]
[*]Postfix to send mail to the ISP.
[*]Getmail to fetch mail from the ISP to my local server.
[*]Dovecot to provide IMAP access to my e-mail.
[*]Roundcube as my e-mail client.
[/LIST]

For that last item, my Roundcube config files indicate that Roundcube sends outgoing e-mail to my local server first, for routing to my ISP.

I created a handy little text file to remind myself how I configured Postfix. Here's a cleaned-up version:

```
When prompted during package install, set up as "Internet with smarthost".
Most of the stuff entered after this will be overwritten, so don't worry
too much.

Create some hash files for use by Postfix:

sudo vim /etc/postfix/generic
  <myname>                    <myname>@<mydomain>
  <myname>@<hostname>.local   <myname>@<mydomain>
  @<hostname>.local           <myname>_local@<mydomain>
# Where <hostname> becomes your local hostname.
sudo postmap hash:/etc/postfix/generic

sudo touch /etc/postfix/sasl_passwd
sudo chmod 0600 /etc/postfix/sasl_passwd
sudo vim /etc/postfix/sasl_passwd
  [<your_isp_smtp_name>]:submission  <username>:<password>
sudo postmap hash:/etc/postfix/sasl_passwd
sudo chmod 0600 /etc/postfix/sasl_passwd*

sudo vim /etc/mailname
  <hostname>.local

Make a backup copy of postfix config file:
sudo cp -v /etc/postfix/main.cf /etc/postfix/main.cf.orig
sudo vim /etc/postfix/main.cf
  myhostname = <hostname>.local
  myorigin = /etc/mailname
  mydestination = <hostname>.local, <hostname>.<your_isp_domain>, localhost.<your_isp_domain>, localhost
  relayhost = [<your_isp_smtp_name>]:submission
  mailbox_command =
  home_mailbox = Maildir/
  inet_protocols = ipv4
  smtp_generic_maps = hash:/etc/postfix/generic
  smtp_sasl_auth_enable = yes
  smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
  smtp_sasl_security_options = noanonymous
sudo service postfix restart

```

Here are my self-instructions for Dovecot:

```
sudo cp /etc/dovecot/conf.d/10-mail.conf /etc/dovecot/conf.d/10-mail.conf.orig
sudo vim /etc/dovecot/conf.d/10-mail.conf
  home_mailbox = Maildir/
sudo service dovecot restart

```

I use a cron job (run every 15 min) under my local host login to run getmail. And here's a sanitized version of my getmailrc file:

```
[retriever]
type = SimpleIMAPRetriever
server = <your_isp_imap_name>
username = <username>
password = <password>

[destination]
type = Maildir
path = ~/Maildir/

[options]
# verbose = 1
read_all = false
delete = false
delete_after = 14

```

---

### Post by lisati on 2013-03-14
> **egpetrich said:**
> I have a server set up to handle my e-mail. There are four parts:

[LIST=1]
[*]Postfix to send mail to the ISP.
[*]Getmail to fetch mail from the ISP to my local server.
[*]Dovecot to provide IMAP access to my e-mail.
[*]Roundcube as my e-mail client.
[/LIST]

My setup is similar, and when I'm at home I use Evolution and/or Thunderbird.

I haven't looked into the options for Roundcube, but Squirrelmail (another webmail system) has a plugin that lets you report spam directly to Spamcop. I find this useful when I'm out and about and want to report spam.

---

### Post by HermanAB on 2013-03-15
Depends.  If you want to learn how a mail system works, then install a Postfix/Apache/Roundcube/SpamAsassin thing and after anything from two weeks to three months of banging your head and reading howto guides, you should have a nice mail server.  

If however you just want to install it and get on with life, then nothing beats Citadel for ease of installation. It takes about 20 minutes to run the Easy Install script.

---

### Post by kenmahn on 2013-03-28
I tried to load postfix on the server and decided to down a simulation first. I noticed that MySQL was to be installed. However, I do not want that since I have Postgresql already running on the server. Also, there looked to be a few other packages that were to be downloaded at the same time that I do not need since I do not have any GUI installed on the server.  

Is there a way to download and install only the postfix package by itself? 

I also have Apache and PHP installed on the server. I do not use perl or  python at all. Will either of the two packages be installed also?

Thanks
Ken

---

### Post by CharlesA on 2013-03-29
postfix doesn't depend on mysql, at least the last time I checked, it didn't.

Are you sure you didn't install any extra packages?

```
apt-rdepends postfix | grep sql
Reading package lists... Done
Building dependency tree
Reading state information... Done
  Depends: libsqlite3-0 (>= 3.5.9)
libsqlite3-0

```

---

### Post by darkod on 2013-03-29
> **HermanAB said:**
> Depends.  If you want to learn how a mail system works, then install a Postfix/Apache/Roundcube/SpamAsassin thing and after anything from two weeks to three months of banging your head and reading howto guides, you should have a nice mail server.  

If however you just want to install it and get on with life, then nothing beats Citadel for ease of installation. It takes about 20 minutes to run the Easy Install script.

Thanks for the idea. Just yesterday I decided to do a test install of Citadel in VBox and my first attempt was with apt-get install citadel-suite, but it didn't work (by default). Since it was only a quick test I didn't bother to investigate right away, but I did expect it to install and work by default.

This morning tried the Easy Install script and worked right away.

Too bad I can't fully test it since I used a dummy local domain so Yahoo and Gmail decline the mails coming from it. :)

But I guess declining an email message is also a proof Citadel is correctly sending it out. :)

---

### Post by SeijiSensei on 2013-03-29
> **CharlesA said:**
> postfix doesn't depend on mysql, at least the last time I checked, it didn't.

I suspect he installed some version of Courier.  

OP, it appears there are both MySQL and PostgreSQL implementations for Courier authentication:  courier-authlib-mysql and courier-authlib-postgresql.

---

### Post by CharlesA on 2013-03-29
Dovecot can use MySQL as well, if I recall correctly.

Nice catch.

---

### Post by kenmahn on 2013-04-04
I installed apt-rdepends and ran it. I got the same answer as charlesa did.

What I did was to run apt-get using "postfix*" installed of just postfix. When I ran it with just postfix, the simulation showed that only postfix would be installed and recommended some others. When I was using "postfix*", it selected everything beginning with postfix and then added the other packages.

Regards,
Ken

---

### Post by darkod on 2013-04-04
> **kenmahn said:**
> I installed apt-rdepends and ran it. I got the same answer as charlesa did.

What I did was to run apt-get using "postfix*" installed of just postfix. When I ran it with just postfix, the simulation showed that only postfix would be installed and recommended some others. When I was using "postfix*", it selected everything beginning with postfix and then added the other packages.

Regards,
Ken

I believe you need to use 'apt-get install postfix' only. As you noticed yourself, it will add all dependant packages. No need to use postfix* because that will add other things too (not sure which ones exactly). I have done it with only postfix and it works, and the official instructions use only postfix too.

---

