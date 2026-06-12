---
title: "Setting up email on server"
date: 2016-09-25
forum: Server Platforms
---

### Post by micahpage on 2016-09-25
[B]my goal:
[/B]I only have a forum on my site. So all i want to accomplish is sending email activation and/or emails regarding lost password resets, etc. I currently have SMTP going through my gmail account to send emails on the server. But i want it to display to users as [EMAIL="admin@python-forum.io"]admin@python-forum.io[/EMAIL].
Do i even need sendmail to do this? 

[B]domain:
[/B]python-forum.io / python-forum.net

[B]Server info:
[/B]Its a LAMP server setup by Digital Ocean. MyBB forum software. 

[B]steps I have taken:

[/B]```
[COLOR=#242729][FONT=Consolas]sudo apt-get install sendmail[/FONT][/COLOR]
```
```
[COLOR=#242729][FONT=Consolas]sudo sendmailconfig[/FONT][/COLOR]
```
and y to everything it asked. 
```
sudo service sendmail start
```
Then if i do
```
metulburr /var/www/python-forum.io $ echo "My test email being sent from sendmail" | /usr/sbin/sendmail micahpage911@yahoo.com


```
it hangs for 60 seconds or so. Im not sure if that was the destination email? But i did not receive it

---

### Post by SeijiSensei on 2016-09-25
First, install the **mailutils** package and use the "mail" program rather than sendmail itself to send messages from the command prompt.
```
echo "This is only a test!" | mail -s 'test message' user@example.com
```

You'll need to get deeper into sendmail if you want to do things like "masquerade" the outbound domain or rewrite senders.  I'd start here: [http://www.tldp.org/HOWTO/Sendmail-Address-Rewrite-3.html](http://www.tldp.org/HOWTO/Sendmail-Address-Rewrite-3.html)

---

### Post by micahpage on 2016-09-25
That tutorials leads to even more questions
> [COLOR=#000000][FONT=&amp]If you aren't using a Debian system, you should replace the word "debian" by "linux" here[/FONT][/COLOR]
Is that if the linux distro is based on debian or debian itself? Such as Ubuntu? 

> ```
[COLOR=#000000]define(`SMART_HOST',`mail-out.your.provider')[/COLOR]
```[HR][/HR][COLOR=#000000][FONT=&amp]Please replace [/FONT][/COLOR]*mail-out.your.provider*[COLOR=#000000][FONT=&amp] by the fully qualified hostname of your internet service provider.[/FONT][/COLOR]
What is the hostname suppose to be for a server on the cloud?[ATTACH=CONFIG]271346[/ATTACH]
I put python-gaming as that i believe is the name of the droplet. 


> [COLOR=#000000][FONT=&amp]Just put the fully qualified host name of your machine into the file [/FONT][/COLOR]/etc/mail/genericsdomain[COLOR=#000000][FONT=&amp].[/FONT][/COLOR]
This file does not exist on my server after getting there on that tutorial

So this is my sendmail.mc file afterwords. 
```
[COLOR=#000000]divert[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]1[/COLOR][COLOR=#000000])[/COLOR][COLOR=#000000]dnl[/COLOR][COLOR=#669933]*#-----------------------------------------------------------------------------*[/COLOR]
[COLOR=#669933]*# $Sendmail: debproto.mc,v 8.14.4 2014-02-11 13:02:08 cowboy Exp $*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# Copyright (c) 1998-2010 Richard Nelson.  All Rights Reserved.*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# cf/debian/sendmail.mc.  Generated from sendmail.mc.in by configure.*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# sendmail.mc prototype config file for building Sendmail 8.14.4*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# Note: the .in file supports 8.7.6 - 9.0.0, but the generated*[/COLOR]
[COLOR=#669933]*#	file is customized to the version noted above.*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# This file is used to configure Sendmail for use with Debian systems.*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# If you modify this file, you will have to regenerate /etc/mail/sendmail.cf*[/COLOR]
[COLOR=#669933]*# by running this file through the m4 preprocessor via one of the following:*[/COLOR]
[COLOR=#669933]*#	* make   (or make -C /etc/mail)*[/COLOR]
[COLOR=#669933]*#	* sendmailconfig *[/COLOR]
[COLOR=#669933]*#	* m4 /etc/mail/sendmail.mc > /etc/mail/sendmail.cf*[/COLOR]
[COLOR=#669933]*# The first two options are preferred as they will also update other files*[/COLOR]
[COLOR=#669933]*# that depend upon the contents of this file.*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*# The best documentation for this .mc file is:*[/COLOR]
[COLOR=#669933]*# /usr/share/doc/sendmail-doc/cf.README.gz*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*#-----------------------------------------------------------------------------*[/COLOR]
divert(0)dnl
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*#   Copyright (c) 1998-2005 Richard Nelson.  All Rights Reserved.*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
[COLOR=#669933]*#  This file is used to configure Sendmail for use with Debian systems.*[/COLOR]
[COLOR=#669933]*#*[/COLOR]
define(`_USE_ETC_MAIL_[COLOR=#CC9933]**')dnl**[/COLOR]
include(`/usr/share/sendmail/cf/m4/cf.m4[COLOR=#CC9933]**')dnl**[/COLOR]
dnl[COLOR=#669933]*#VERSIONID(`$Id: sendmail.mc, v 8.14.4-4.1ubuntu1 2014-02-11 13:02:08 cowboy Exp $')*[/COLOR]
VERSIONID(`sendmail.mc - metulbot[COLOR=#888888]@gmail.com[/COLOR][COLOR=#CC9933]**')**[/COLOR]
OSTYPE(`debian[COLOR=#CC9933]**')dnl**[/COLOR]
define([COLOR=#CC9933]**`ALIAS_FILE',`**[/COLOR]/etc/mail/aliases[COLOR=#CC9933]**')**[/COLOR]
DOMAIN(`debian-mta[COLOR=#CC9933]**')dnl**[/COLOR]
dnl [COLOR=#669933]*# Items controlled by /etc/mail/sendmail.conf - DO NOT TOUCH HERE*[/COLOR]
undefine(`confHOST_STATUS_DIRECTORY[COLOR=#CC9933]**')dnl        #DAEMON_HOSTSTATS=**[/COLOR]





FEATURE(masquerade_envelope) 
FEATURE(genericstable, `[COLOR=#00AAAA]hash[/COLOR] -o /etc/mail/genericstable[COLOR=#CC9933]**')**[/COLOR]
GENERICS_DOMAIN_FILE(`/etc/mail/genericsdomain[COLOR=#CC9933]**') **[/COLOR]


define([COLOR=#CC9933]**`SMART_HOST',`**[/COLOR]python-gaming[COLOR=#CC9933]**')**[/COLOR]

dnl [COLOR=#669933]*# Items controlled by /etc/mail/sendmail.conf - DO NOT TOUCH HERE*[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# General defines*[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# SAFE_FILE_ENV: [undefined] If set, sendmail will do a chroot()*[/COLOR]
dnl [COLOR=#669933]*#	into this directory before writing files.*[/COLOR]
dnl [COLOR=#669933]*#	If *all* your user accounts are under /home then use that*[/COLOR]
dnl [COLOR=#669933]*#	instead - it will prevent any writes outside of /home !*[/COLOR]
dnl [COLOR=#669933]*#   define(`confSAFE_FILE_ENV',             `')dnl*[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# Daemon options - restrict to servicing LOCALHOST ONLY !!!*[/COLOR]
dnl [COLOR=#669933]*# Remove `, Addr=' clauses to receive from any interface*[/COLOR]
dnl [COLOR=#669933]*# If you want to support IPv6, switch the commented/uncommentd lines*[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
FEATURE(`no_default_msa[COLOR=#CC9933]**')dnl**[/COLOR]
dnl DAEMON_OPTIONS(`Family=inet6, Name=MTA-v6, Port=smtp, Addr=::1[COLOR=#CC9933]**')dnl**[/COLOR]
DAEMON_OPTIONS(`Family=inet,  Name=MTA-v4, Port=smtp, Addr=127.0.0.1[COLOR=#CC9933]**')dnl**[/COLOR]
dnl DAEMON_OPTIONS(`Family=inet6, Name=MSP-v6, Port=submission, M=Ea, Addr=::1[COLOR=#CC9933]**')dnl**[/COLOR]
DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission, M=Ea, Addr=127.0.0.1[COLOR=#CC9933]**')dnl**[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# Be somewhat anal in what we allow*[/COLOR]
define(`confPRIVACY_FLAGS[COLOR=#CC9933]**',dnl**[/COLOR]
`needmailhelo,needexpnhelo,needvrfyhelo,restrictqrun,restrictexpand,nobodyreturn,authwarnings[COLOR=#CC9933]**')dnl**[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# Define connection throttling and window length*[/COLOR]
define([COLOR=#CC9933]**`confCONNECTION_RATE_THROTTLE', `**[/COLOR]15[COLOR=#CC9933]**')dnl**[/COLOR]
define([COLOR=#CC9933]**`confCONNECTION_RATE_WINDOW_SIZE',`**[/COLOR]10m[COLOR=#CC9933]**')dnl**[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# Features*[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# use /etc/mail/local-host-names*[/COLOR]
FEATURE(`use_cw_file[COLOR=#CC9933]**')dnl**[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# The access db is the basis for most of sendmail's checking*[/COLOR]
FEATURE([COLOR=#CC9933]**`access_db', , `**[/COLOR]skip[COLOR=#CC9933]**')dnl**[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# The greet_pause feature stops some automail bots - but check the*[/COLOR]
dnl [COLOR=#669933]*# provided access db for details on excluding localhosts...*[/COLOR]
FEATURE([COLOR=#CC9933]**`greet_pause', `**[/COLOR]1000[COLOR=#CC9933]**')dnl 1 seconds**[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# Delay_checks allows sender<->recipient checking*[/COLOR]
FEATURE([COLOR=#CC9933]**`delay_checks', `**[/COLOR]friend[COLOR=#CC9933]**', `n'**[/COLOR])dnl
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# If we get too many bad recipients, slow things down...*[/COLOR]
define([COLOR=#CC9933]**`confBAD_RCPT_THROTTLE',`**[/COLOR]3[COLOR=#CC9933]**')dnl**[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# Stop connections that overflow our concurrent and time connection rates*[/COLOR]
FEATURE([COLOR=#CC9933]**`conncontrol', `**[/COLOR]nodelay[COLOR=#CC9933]**', `terminate'**[/COLOR])dnl
FEATURE([COLOR=#CC9933]**`ratecontrol', `**[/COLOR]nodelay[COLOR=#CC9933]**', `terminate'**[/COLOR])dnl
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# If you're on a dialup link, you should enable this - so sendmail*[/COLOR]
dnl [COLOR=#669933]*# will not bring up the link (it will queue mail for later)*[/COLOR]
dnl define([COLOR=#CC9933]**`confCON_EXPENSIVE',`**[/COLOR][COLOR=#00AAAA]True[/COLOR][COLOR=#CC9933]**')dnl**[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# Dialup/LAN connection overrides*[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
include(`/etc/mail/m4/dialup.m4[COLOR=#CC9933]**')dnl**[/COLOR]
include(`/etc/mail/m4/provider.m4[COLOR=#CC9933]**')dnl**[/COLOR]
dnl [COLOR=#669933]*#*[/COLOR]
dnl [COLOR=#669933]*# Default Mailer setup*[/COLOR]
MAILER_DEFINITIONS
MAILER(`local[COLOR=#CC9933]**')dnl**[/COLOR] [COLOR=#000000]MAILER[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000]`[/COLOR][COLOR=#000000]smtp[/COLOR][COLOR=#CC9933]**')dnl**[/COLOR]
```

---

### Post by micahpage on 2016-09-25
So i found another how to
[https://linuxconfig.org/configuring-gmail-as-sendmail-email-relay](https://linuxconfig.org/configuring-gmail-as-sendmail-email-relay)

I reverted my sendmail.mc file back to default and went through the steps specified in that tutorial.

After doing this is does send an email to that address
```
root /etc/mail # echo "Just testing my sendmail gmail relay" | mail -s "Sendmail gmail Relay" sondra.parkin@gmail.com


```
[ATTACH=CONFIG]271347[/ATTACH]

But it shows as root [EMAIL="metulbot@gmail.com"]metulbot@gmail.com[/EMAIL]


After this setup, i switched the forum software from SMTP to PHP mail. And ran a test for a lost password email
[ATTACH=CONFIG]271349[/ATTACH][ATTACH=CONFIG]271348[/ATTACH]
It appears as Python Forums <> [EMAIL="metulbot@gmail.com"]metulbot@gmail.com[/EMAIL]

The fact that its entitled by "Python Forums <>" instead of "metulbot" makes it more appealing to just leave it as it is. I didnt realize the complexity of setting up email for the forum.  One question...where is the <> on the title coming from and how can i get rid of it?

---

### Post by SeijiSensei on 2016-09-25
The "<>" means the sender has no email address.  You can't get rid of it since a standard RFC822 email address is
```
Some User <someuser@domain>
```
"Python Forums" doesn't map to a user on your system so the software doesn't know what to fill in for the email address and leaves it empty.  Obviously that also means no one can reply to these messages if needed.

---

### Post by micahpage on 2016-09-26
It shows [email]metulbot@gmail.com[/email] afterwords though. so more like
```
Python Forums <> <metulbot@gmail.com>
```

Thanks for the help. I think i will just leave it as is for now. Maybe another day down the road i will fix it. But for now i have had my fill of it.

> [COLOR=#000000]Obviously that also means no one can reply to these messages if needed.[/COLOR]
As long as i can send email out for an email activation and lost passwords, that all i needed. I dont believe you receive any emails back regarding that?

---

### Post by SeijiSensei on 2016-09-26
Just make sure you include some email address in the message that people can use to respond in case they are having difficulties.  Nothing annoys people more than having some problem without any way to contact someone to resolve it.

---

### Post by micahpage on 2016-09-26
> [COLOR=#000000]Nothing annoys people more than having some problem without any way to contact someone to resolve it.[/COLOR]
I can put in our IRC channel and info


I checked the mail logs in /var/log/mail.log and it reads over and over
> Sep 26 12:00:01 python-gaming sm-msp-queue[2539]: My unqualified host name (python-gaming) unknown; sleeping for retry
Sep 26 12:01:01 python-gaming sm-msp-queue[2539]: unable to qualify my own domain name (python-gaming) -- using short name




---

### Post by SeijiSensei on 2016-09-27
That's fine for people who use IRC.  I'm not one of them, so that wouldn't help me.  Give them a reply email address.

As for the error, read this: [http://serverfault.com/questions/58363/my-unqualified-host-name-foo-bar-unknown-problem](http://serverfault.com/questions/58363/my-unqualified-host-name-foo-bar-unknown-problem)

I find that simply handing the error string to Google gets me good answers most of the time.

---

### Post by micahpage on 2016-09-27
> [COLOR=#000000]That's fine for people who use IRC. I'm not one of them, so that wouldn't help me. Give them a reply email address.[/COLOR]
A reply email to send to whom? There is IRC embedded within the site that people can use if the dont want to use a client. None of the admins check emails, yet all of them check the IRC. So it seems reasonable to put IRC. Even if i had it as [EMAIL="metulbot@gmail.com"]metulbot@gmail.com[/EMAIL] as response, that is just a junk email that no one logs into unless for junk stuff. No one would see a reply anyways. Whereas IRC someone could could immediate help, one on one.  

> [COLOR=#000000]I find that simply handing the error string to Google gets me good answers most of the time.[/COLOR]
Yeah i know, otherwise i wouldnt of asked. THis is my hosts file that makes that error

> # Your system has configured 'manage_etc_hosts' as True.# As a result, if you wish for changes to this file to persist
# then you will need to either
# a.) make changes to the master file in /etc/cloud/templates/hosts.tmpl
# b.) change or remove the value of 'manage_etc_hosts' in
#     /etc/cloud/cloud.cfg or cloud-config from user-data
127.0.0.1 localhost localhost.localdomain python-forum.io
127.0.1.1 python-gaming python-gaming
127.0.0.1 localhost


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
~                        

---

### Post by SeijiSensei on 2016-09-27
No, you're support to replace "foo.bar" with something like "mail.python-gaming.io" or whatever your server's fully-qualified domain name is.  "localhost.localdomain" is occasionally used as a alias for "localhost".

---

### Post by micahpage on 2016-09-27
where is the mail. coming from in that? 
> [COLOR=#000000]whatever your server's fully-qualified domain name is[/COLOR]
isnt this the domain name python-forum.io?

---

### Post by SeijiSensei on 2016-09-28
Yes, that's the domain name, but individual machines have names of the form host.domain.name, like [www.ubuntuforums.org](www.ubuntuforums.org). See: [https://ist.mit.edu/network/ip](https://ist.mit.edu/network/ip)

---

