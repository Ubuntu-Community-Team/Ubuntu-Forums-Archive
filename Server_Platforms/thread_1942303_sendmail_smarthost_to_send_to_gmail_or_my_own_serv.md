---
title: "sendmail smarthost to send to gmail or my own server"
date: 2012-03-17
forum: Server Platforms
---

### Post by geek.de.nz on 2012-03-17
Hi,

First of all, I apologise, because this seems like a well-discussed topic, but I am posting here anyway, because I couldn't get it working for quite a while now, even though there are lots of tutorials:

I would like to send email from my local machine to my server or gmail's smtp server, because my ISP does not allow my machine to send email (Argh!). I don't mind if there is a gmail header or similar because I just need it to test my local PHP applications like Drupal and CiviCRM.

I followed this first:
[http://darrynvt.wordpress.com/2012/01/04/setup-sendmail-notifications-for-gmail-smtp/](http://darrynvt.wordpress.com/2012/01/04/setup-sendmail-notifications-for-gmail-smtp/)
but it did not work for me.

My /etc/mail/sendmail.mc file:

```
divert(-1)dnl
#-----------------------------------------------------------------------------
# $Sendmail: debproto.mc,v 8.14.4 2011-08-14 09:21:51 cowboy Exp $
#
# Copyright (c) 1998-2010 Richard Nelson.  All Rights Reserved.
#
# cf/debian/sendmail.mc.  Generated from sendmail.mc.in by configure.
#
# sendmail.mc prototype config file for building Sendmail 8.14.4
#
# Note: the .in file supports 8.7.6 - 9.0.0, but the generated
#	file is customized to the version noted above.
#
# This file is used to configure Sendmail for use with Debian systems.
#
# If you modify this file, you will have to regenerate /etc/mail/sendmail.cf
# by running this file through the m4 preprocessor via one of the following:
#	* make   (or make -C /etc/mail)
#	* sendmailconfig 
#	* m4 /etc/mail/sendmail.mc > /etc/mail/sendmail.cf
# The first two options are preferred as they will also update other files
# that depend upon the contents of this file.
#
# The best documentation for this .mc file is:
# /usr/share/doc/sendmail-doc/cf.README.gz
#
#-----------------------------------------------------------------------------
divert(0)dnl
#
#   Copyright (c) 1998-2005 Richard Nelson.  All Rights Reserved.
#
#  This file is used to configure Sendmail for use with Debian systems.
#
define(`_USE_ETC_MAIL_')dnl
include(`/usr/share/sendmail/cf/m4/cf.m4')dnl
VERSIONID(`$Id: sendmail.mc, v 8.14.4-2ubuntu2 2011-08-14 09:21:51 cowboy Exp $')
OSTYPE(`debian')dnl
DOMAIN(`debian-mta')dnl
dnl # Items controlled by /etc/mail/sendmail.conf - DO NOT TOUCH HERE
undefine(`confHOST_STATUS_DIRECTORY')dnl        #DAEMON_HOSTSTATS=
dnl # Items controlled by /etc/mail/sendmail.conf - DO NOT TOUCH HERE
dnl #
dnl # General defines
dnl #
dnl # SAFE_FILE_ENV: [undefined] If set, sendmail will do a chroot()
dnl #	into this directory before writing files.
dnl #	If *all* your user accounts are under /home then use that
dnl #	instead - it will prevent any writes outside of /home !
dnl #   define(`confSAFE_FILE_ENV',             `')dnl
dnl #
dnl # Daemon options - restrict to servicing LOCALHOST ONLY !!!
dnl # Remove `, Addr=' clauses to receive from any interface
dnl # If you want to support IPv6, switch the commented/uncommentd lines
dnl #
FEATURE(`no_default_msa')dnl
dnl DAEMON_OPTIONS(`Family=inet6, Name=MTA-v6, Port=smtp, Addr=::1')dnl
DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1')dnl
dnl DAEMON_OPTIONS(`Family=inet6, Name=MSP-v6, Port=submission, M=Ea, Addr=::1')dnl
DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission, M=Ea, Addr=127.0.0.1')dnl
dnl #
dnl # Be somewhat anal in what we allow
define(`confPRIVACY_FLAGS',dnl
`needmailhelo,needexpnhelo,needvrfyhelo,restrictqrun,restrictexpand,nobodyreturn,authwarnings')dnl
dnl #
dnl # Define connection throttling and window length
define(`confCONNECTION_RATE_THROTTLE', `15')dnl
define(`confCONNECTION_RATE_WINDOW_SIZE',`10m')dnl
dnl #
dnl # Features
dnl #
dnl # use /etc/mail/local-host-names
FEATURE(`use_cw_file')dnl
dnl #
dnl # The access db is the basis for most of sendmail's checking
FEATURE(`access_db', , `skip')dnl
dnl #
dnl # The greet_pause feature stops some automail bots - but check the
dnl # provided access db for details on excluding localhosts...
FEATURE(`greet_pause', `1000')dnl 1 seconds
dnl #
dnl # Delay_checks allows sender<->recipient checking
FEATURE(`delay_checks', `friend', `n')dnl
dnl #
dnl # If we get too many bad recipients, slow things down...
define(`confBAD_RCPT_THROTTLE',`3')dnl
dnl #
dnl # Stop connections that overflow our concurrent and time connection rates
FEATURE(`conncontrol', `nodelay', `terminate')dnl
FEATURE(`ratecontrol', `nodelay', `terminate')dnl
dnl #
dnl # If you're on a dialup link, you should enable this - so sendmail
dnl # will not bring up the link (it will queue mail for later)
dnl define(`confCON_EXPENSIVE',`True')dnl
dnl #
dnl # Dialup/LAN connection overrides
dnl #
include(`/etc/mail/m4/dialup.m4')dnl
include(`/etc/mail/m4/provider.m4')dnl
dnl #

include(`/etc/mail/tls/starttls.m4')dnl
define(`SMART_HOST',`smtp.gmail.com')dnl
define(`confAUTH_MECHANISMS', `EXTERNAL GSSAPI DIGEST-MD5 CRAM-MD5 LOGIN PLAIN')dnl
define(`RELAY_MAILER_ARGS', `TCP $h 587')
define(`ESMTP_MAILER_ARGS', `TCP $h 587')
FEATURE(`authinfo',`hash /etc/mail/auth/client-info')dnl
define(`CERT_DIR', `MAIL_SETTINGS_DIR/certs')
define(`confCACERT_PATH', `CERT_DIR')
define(`confCACERT', `CERT_DIR/CAcert.pem')
define(`confSERVER_CERT', `CERT_DIR/mycert.pem')
define(`confSERVER_KEY', `CERT_DIR/mykey.pem')
define(`confCLIENT_CERT', `CERT_DIR/mycert.pem')
define(`confCLIENT_KEY', `CERT_DIR/mykey.pem')

dnl # Masquerading options
FEATURE(`always_add_domain')dnl
MASQUERADE_AS(`ihostnz.com')dnl
dnl # FEATURE(`allmasquerade')dnl
FEATURE(`masquerade_envelope')dnl
FEATURE(`genericstable')dnl
GENERICS_DOMAIN(`localhost.localdomain')dnl
MASQUERADE_DOMAIN(`galaxy')dnl

dnl # Default Mailer setup
dnl MAILER_DEFINITIONS
dnl define(`SMART_HOST', `ihostnz.com')dnl
dnl MAILER(`local')dnl
dnl MAILER(`smtp')dnl

```

My hostname is galaxy.

My /var/log/mail.log file:
```
Mar 18 00:59:14 galaxy sendmail[6762]: unable to qualify my own domain name (galaxy) -- using short name
Mar 18 00:59:15 galaxy sendmail[6762]: q2HBxEul006762: from=geekdenz, size=86, class=0, nrcpts=1, msgid=<201203171159.q2HBxEul006762@galaxy>, relay=geekdenz@localhost
Mar 18 00:59:15 galaxy sm-mta[7315]: STARTTLS=server, relay=localhost [127.0.0.1], version=TLSv1/SSLv3, verify=NOT, cipher=DHE-DSS-AES256-SHA, bits=256/256
Mar 18 00:59:15 galaxy sendmail[6762]: STARTTLS=client, relay=[127.0.0.1], version=TLSv1/SSLv3, verify=FAIL, cipher=DHE-DSS-AES256-SHA, bits=256/256
Mar 18 00:59:15 galaxy sm-mta[7315]: q2HBxF4d007315: SYSERR(root): buildaddr: unknown mailer unknown
Mar 18 00:59:15 galaxy sendmail[6762]: q2HBxEul006762: to=<th.heuer@gmail.com>, ctladdr=geekdenz (1000/1000), delay=00:00:01, xdelay=00:00:00, mailer=relay, pri=30086, relay=[127.0.0.1] [127.0.0.1], dsn=5.3.5, stat=Service unavailable
Mar 18 00:59:15 galaxy sm-mta[7315]: q2HBxF4d007315: from=<geekdenz@galaxy>, size=86, class=0, nrcpts=0, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Mar 18 01:00:01 galaxy sm-msp-queue[7766]: My unqualified host name (galaxy) unknown; sleeping for retry
Mar 18 01:01:01 galaxy sm-msp-queue[7766]: unable to qualify my own domain name (galaxy) -- using short name
```

There is always a long delay when I send an email like:
```
echo test email | mail -s mysubject my@gmail.com
```

Help! I really need it because I've been stuck on this for many hours now and I need to get the project off the ground.

Using Ubuntu 11.10.

Many thanks!

---

### Post by Demented ZA on 2012-03-17
First off, for what you are trying to do, I would use postfix rather than sendmail. Postfix was adapted from sendmail, but is > ...an alternative to the widely-used [Sendmail]("http://www.sendmail.org/") program.     Postfix attempts to be fast, easy to administer, and secure. from thier website.

There's a guide for reference here:

[https://help.ubuntu.com/8.04/serverguide/C/postfix.html](https://help.ubuntu.com/8.04/serverguide/C/postfix.html)

But you wouldn't need to do everything in that guide, as a lot of it is security that you don't need if you are not relaying mail for clients outside your network.

If you are using it for sending mail only, I wouldn't worry about what mailbox type to choose as you won't be using it. If you think you might start using it later, use Maildir as its easy enough to work with.

Finally, for relaying mail, you will need to authenticate against the Gmail server or it won't let you do anything. Just have a look here:

[http://www.dnsexit.com/support/mailrelay/postfix.html](http://www.dnsexit.com/support/mailrelay/postfix.html)

Looking at your post above, you are relaying mail via localhost, in other words, once your server is recieving mail, it sees that it is not the delivery location for your mail, and then refers to the relay host which is localhost (itself), and will be sitting with the same problem all over. Do you see the problem?

I assume you don't have a domain, a static internet IP for your server, and that you don't have an MX record pointing to your static ip from the DNS of your domian? If you don't know what I'm talking about, then the first part of my post is all you need.

Hope that helps

---

### Post by geek.de.nz on 2012-03-17
> **Demented ZA said:**
> 
[http://www.dnsexit.com/support/mailrelay/postfix.html](http://www.dnsexit.com/support/mailrelay/postfix.html)


This did the trick! Thanks so much! Also added a post to my blog so that I don't loose this info @ [http://www.thheuer.com/2012/03/smtp-postfix-server-setup-for-your-home-development/](http://www.thheuer.com/2012/03/smtp-postfix-server-setup-for-your-home-development/).

I ended up using my ISP's smtp server. Why do they block port 25 when one can just use their smtp server to spam??

I guess they have a bit more control then. So if they detect a spammer, they can block that machine, but still...

---

### Post by Demented ZA on 2012-03-20
Awesome, glad it helped.

Your isp doesn't allow anyone to connect to their smtp server, only clients on their network, such as you. Connecting to the smtp server from your isp, serves as a method of authentication to the smtp server and will help to identify you in case they need to trace those nasty spammers.

They block port 25 for security. Spam has very little to do with it.

---

### Post by geek.de.nz on 2012-03-20
Thanks for the insight!

---

### Post by smtp on 2012-04-23
There were a problem with your sendmail configuration, was not need to exchange it with postfix :-)

Simply uncomment: dnl MAILER(`smtp')dnl -> MAILER(`smtp')dnl would do the magic.

---

### Post by sasa.tomic on 2012-10-25
Configuring postfix (sendmail) is certainly not easy. I made a small user-friendly script for a no-questions-asked installation and configuration of postfix with Gmail.

The script configures postfix to relay mail to smtp.gmail.com (which will send your emails to the world). Check out the [https://gist.github.com/3952294](https://gist.github.com/3952294)
and please tell me if it works for you (or not)

P.S. I checked the script on Ubuntu 12.04, but it should work on previous versions as well. Before running the script, uninstall everything you manually configured on your machine (e.g. exim4 maybe), and also, you should consider purging postfix with

```
sudo apt-get purge postfix
```

---

