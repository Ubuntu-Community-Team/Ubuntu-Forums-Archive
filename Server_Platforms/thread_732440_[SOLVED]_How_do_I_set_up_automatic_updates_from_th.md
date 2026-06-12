---
title: "[SOLVED] How do I set up automatic updates from the command line?"
date: 2008-03-22
forum: Server Platforms
---

### Post by MountainX on 2008-03-22
I'd like to have security updates downloaded and installed automatically on my server on a daily basis. How do I set that up? Thanks.

---

### Post by brownknight on 2008-03-22
Hi. You can do this...

Open up the crontab as root

    kvaes@ubuntu:~$ sudo crontab -e

Add the following line to your crontab

    0 0 * * * aptitude -y update && aptitude -y upgrade && aptitude -y dist-upgrade && aptitude -y autoclean

I found this from this blog:  [http://www.kvaes.be/ubuntu/setting-up-auto-update-on-your-system-thru-command-line/](http://www.kvaes.be/ubuntu/setting-up-auto-update-on-your-system-thru-command-line/)

---

### Post by MountainX on 2008-03-22
Thank you. That looks like it will give me a lot more than security updates. I'll try it. I'm running Hardy beta, so this should upgrade me to the release. Maybe I'll leave off the dist-upgrade part though. I like Hardy because it is LTS. Thanks again.

BTW, there have to be spaces between each of those stars. They mean all days, months and years.

UPDATE:
I decided to use loopiv's suggestion instead. See next item in this thread.

---

### Post by loopiv on 2008-03-23
Another way to perform auto-updates (at least on my 6.06 LTS box) is by using the "unattended-upgrades" package.  Just do a
```
apt-get install unattended-upgrades
``` and then edit /etc/apt/apt.conf.d/50unattended-upgrades to your liking.

---

### Post by MountainX on 2008-03-23
Thank you loopiv. That sounds good. 

I think there is a problem with the other method. Here are some links I was reading:
[http://brainstorm.ubuntu.com/idea/2981/](http://brainstorm.ubuntu.com/idea/2981/)
[http://brainstorm.ubuntu.com/contributor/brettalton/](http://brainstorm.ubuntu.com/contributor/brettalton/)

---

### Post by MountainX on 2008-03-23
> **loopiv said:**
> Another way to perform auto-updates (at least on my 6.06 LTS box) is by using the "unattended-upgrades" package.  Just do a
```
apt-get install unattended-upgrades
``` and then edit /etc/apt/apt.conf.d/50unattended-upgrades to your liking.

I want to set up the email for upgrade problems. What is the most light weight mail setup possible. I won't use it for anything else other than to send myself error messages. Is there something that will just send through my gmail account? Thanks.

---

### Post by brownknight on 2008-03-23
thanks loopiv

---

### Post by chemist109 on 2008-04-02
MountainX:

Try this to solve your e-mail sending problems:

[http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)

It's a Perl program that uses an smtp server to send mails (it's not an MTA).  It should work with GMail just fine.

---

### Post by MountainX on 2008-04-02
> **chemist109 said:**
> MountainX:

Try this to solve your e-mail sending problems:

[http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)

It's a Perl program that uses an smtp server to send mails (it's not an MTA).  It should work with GMail just fine.

Thanks. It does sound like the most recent versions will work with gmail. Gmail requires TLS. See _TLS Support_ below. (Extra modules are required.)

See "sendmail with gmail?" here:
[http://www.debianhelp.org/node/5133](http://www.debianhelp.org/node/5133)

sendEmail -f [email]my.account@gmail.com[/email] -t [email]myself@domain.tld[/email] \
-u test -m "this is a test" \
-s smtp.gmail.com \
-o tls=yes \
-xu my.account -xp mypasswd

With the appropriate values for -f, -t, -xu and -xp, the mail is sent
successfully and arrives as expected.


_TLS Support_
Starting with sendEmail v1.54, TLS support is included! To enable TLS support simply install the Net::SSLeay and IO::Socket::SSL perl modules. The following new command line parameters are now available:
    -o tls=auto This is the default, TLS will be used if possible.
    -o tls=yes Use this to require TLS for message delivery.
    -o tls=no Use this to disable TLS support.
If TLS is giving strange errors, try upgrading the Net::SSLeay and IO::Socket::SSL perl modules. Please do NOT report TLS bugs unless you have already done this! If you're running up-to-date versions of these modules and you are getting TLS errors, your detailed bug report will be appreciated. Yes, you can finally use SendEmail to send messages to your GMail account :)

---

