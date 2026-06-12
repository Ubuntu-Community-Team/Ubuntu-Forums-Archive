---
title: "Do I need to run a mail server on my web server?"
date: 2008-11-13
forum: Server Platforms
---

### Post by lpoppleton on 2008-11-13
A similar question was already asked a couple of years ago in thread [http://ubuntuforums.org/showthread.php?t=308453](http://ubuntuforums.org/showthread.php?t=308453), but the answers were not helpful to me because I don't want to run a mail server.

I am running 8.04 server (with desktop added on for ease of use) as a LAMP server.  I am writing php programs that require use of php mail() to send out notifications and confirmations from web services.  I have no need of a mail server, nor do I want the extra overhead.  According to everything I have read in PHP, I should be able to use the mail() function by specifying the appropriate parameters (SMTP, smtp_port and sendmail_from) in php.ini to send the mail out to another mail server on the network.  It doesn't work.
With postfix installed, postfix intercepts the messages and they don't go out.  I uninstalled postfix but I still cannot get mail out from my php programs.

This has to be a fairly common issue, but I have not been able to find any resolution other than "Install Postfix".  Is this really necessary?
Thanks.

---

### Post by wizard10000 on 2008-11-13
Yeah, it's really necessary.

In order for a LAMP server to send email it has to communicate with a local MTA (mail transfer agent).  Postfix is one, sendmail is another - there are lots more.

The three functions you mention are Windows only.  See [http://www.w3schools.com/PHP/php_ref_mail.asp](http://www.w3schools.com/PHP/php_ref_mail.asp)

Good luck  ;)

---

### Post by hictio on 2008-11-13
You need to enable the service (be sendmail or whatever) but you don't to run a mail server per se, that is, listening to connections over the network, etc.
By simply listening over the loopback you'll be able to send emails from your box*.

*Your box must have a registered domain, a valid PTR record, and valid, non dinamic IP address; or you'll get a lot of bounced emails due to SPAM fighting/ RBL DNS lists.

One option might be, if needed, to configure your mailserver to relay the email to your ISP's SMTP server.

---

### Post by hagen00 on 2008-11-13
it's not a trainsmash to install Postfix. The "overhead" is totally a non issue. Like sneezing at the ocean.

---

### Post by lpoppleton on 2008-11-13
Thank you Wizard10000 and hictio.  I had read the info at the posted php link, but then read another that said you could actually do the windows thing from a linux machine as long as you had a valid smtp server that would accept mail from you.  I have been running a similar setup on an AIX box for years and it worked fine, but I think it grabbed the sendmail binaries without actually having to run sendmail as a daemon.  I know that installing postfix is no big deal, but didn't want to run it if I didn't need to.  Your answer is I need to run a mail server, so I will.  Thanks!

---

### Post by kustomjs on 2008-11-13
you could use google apps and setup php mailer inside of your directory. so you dont have to worry about setting up spam filters and that kind. because I am using google apps just fine and it works.

---

### Post by Dr Small on 2008-11-13
This should be all you need to send mail from php scripts with the mail() function:
```
drsmall@mycroft:~$ mail
The program 'mail' can be found in the following packages:
 * mailx
 * mailutils
Try: sudo apt-get install <selected package>

```

---

### Post by MJN on 2008-11-13
If all you want is outgoing mail to support then check out [nullmailer]("http://untroubled.org/nullmailer/") - it is a bare bones MTA that will relay outbound mail via your ISP's mail server for any mail-enabled app you might have (including PHP mail).

It's basically everything you want and need from a fully-blown MTA like Postfix, without all of the stuff you don't.

Mathew

---

