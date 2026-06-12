---
title: "postfix authentication problem with comcast"
date: 2010-06-29
forum: Server Platforms
---

### Post by nycterfin on 2010-06-29
Hello. I've been trying to set up postfix to relay messages through comcast on port 587 and so far I can receive messages just fine, but whenever I try to send messages, in /var/log/mail.log I see
> host smtp.comcast.net[76.96.62.117] said: 550
5.1.0 Authentication required (in reply to MAIL FROM command)

I use Ubuntu Server 8.10 LTS (32-bit version). Dovecot is also installed and used for SASL (at least I think it is used for SASL. I've tied quite a few guides that used different settings). I do have a passwd file that contains my comcast email account credentials (i.e. email address and password). I have forwarded both ports 587 and 25 to the ubuntu server box that is running postfix and dovecot. I connect to the ubuntu box from a windows box which are both on the same network in my house. Since the log is reporting that authentication is required and not that authentication has failed, I wonder if postfix is even sending my credentials. Any ideas on how to fix this issue?

---

### Post by three_jeeps on 2010-06-29
I am attempting the same thing.  Have you seen these posts:
[http://www.justatheory.com/computers/mail/postfix-and-comcast.html](http://www.justatheory.com/computers/mail/postfix-and-comcast.html)
[http://bcn.boulder.co.us/~neal/cablemail.html](http://bcn.boulder.co.us/~neal/cablemail.html)
[http://www.pdxtc.com/wpblog/technology-articles/cant-send-mail-using-comcast/](http://www.pdxtc.com/wpblog/technology-articles/cant-send-mail-using-comcast/)
[http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/](http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/)
[http://www.davidgrant.ca/setting_up_postfix_to_send_outgoing_mail_on_ubuntu](http://www.davidgrant.ca/setting_up_postfix_to_send_outgoing_mail_on_ubuntu)

I included some articles about going through gmail because the idea is the same, but the approaches differed a bit.
Am curious if you have seen these and if any of them solved your problem...
-J

---

### Post by nycterfin on 2010-06-29
Thanks, three_jeeps, for the reply. I definitely have seen and followed the guide at [http://www.justatheory.com/computers/mail/postfix-and-comcast.html](http://www.justatheory.com/computers/mail/postfix-and-comcast.html). The others you have posted I do not believe I have seen yet and those that use gmail I know I have not attempted. I guess I will give it a shot, though, since relaying through comcast does not seem to be working.
 
Have you had any luck with your setup? Well, I'm off to try some of these guides. I wish you the best of luck with your setup. I'll report back about the outcome of these guides.
 
If anyone else has some insight, please do share.

---

### Post by jimav on 2011-09-08
A good reference is [http://www.postfix.org/SOHO_README.html](http://www.postfix.org/SOHO_README.html)

The key requirements are:
[LIST=1]
[*]Tell postscript to use SASL login authentication, and supply your comcast.net username & password
[*]Map "return" email addresses, which by default use your fantasy host name, to valid external email addresses.
[/LIST]
Here is a procedure which worked for me on Ubuntu 10.10 'Maverick':

$ sudo apt-get purge postfix     # start fresh; rm old config files
$ sudo apt-get install mailutils # or just postfix if you already have /bin/mail etc.
$ sudo dpkg-reconfigure postfix  # if not prompted for config during install

Select 'Internet with smarthost'
System mail name: localhost.local
SMTP relay host:  [smtp.comcast.net]:587

$ confdir=`postconf -h config_directory`  # /etc/postfix on my system
$ Add/change in $confdir/main.cf:

```
smtp_generic_maps = hash:${config_directory}/generic
smtp_enforce_tls = no
smtp_sasl_auth_enable = yes
smtp_sasl_security_options =
smtp_sasl_password_maps = hash:${config_directory}/sasl/passwd

```
$ Create $confdir/sasl/passwd:
```
smtp.comcast.net *yourcomcastusername*:*yourcomcastpassword*
```
$ chown root:root $confdir/sasl/passwd
$ chmod 600 $confdir/sasl/passwd
$ postmap $confdir/sasl/passwd

$ Create $confdir/generic:

```
# Map generated Return-Path email addresses to real email addresses
# at an external email service.
# The @localhost.local entry causes -all- email from local users not
# previously listed to appear to be from yourgmaillogname@gmail.com
# (you can leave this off)
harry@localhost.local  harry.potter@gmail.com
mary@localhost.local  mary123@yahoo.com
@localhost.local  yourgmaillogname@gmail.com

```
$ chown root:root $confdir/generic
$ chmod 600 $confdir/generic
$ postmap $confdir/generic

$ postfix reload

# Now test it out
echo "Testing" | /bin/mail -s "testing via postscript" [email]yourlogin@gmail.com[/email]

$ tail -25 /etc/log/syslog   # should show "mail accepted for delivery"

---

