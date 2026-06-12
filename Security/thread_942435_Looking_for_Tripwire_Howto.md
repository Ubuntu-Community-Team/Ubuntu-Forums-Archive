---
title: "Looking for Tripwire Howto"
date: 2008-10-09
forum: Security
---

### Post by spikoley on 2008-10-09
I am looking for Tripwire HowTo with Ubuntu.  The ones I have found online do not explain the config file or how to get Tripwire to send email alerts.  It would be great if somebody wrote an Ubuntu specific Tripwire Howto.

---

### Post by cariboo on 2008-10-09
Not sure about the howto, but when you install tripwire a cron job is installed that runs tripwire daily and sends you and emails of the results. The file is located in /etc/cron.daily and is called tripwire.

Jim

---

### Post by ice60 on 2008-10-09
i have this bookmarked, i've never used it though!
[http://www.linuxhelp.net/guides/tripwire/](http://www.linuxhelp.net/guides/tripwire/)

---

### Post by teledyn on 2010-07-04
> **ice60 said:**
> i have this bookmarked, i've never used it though!
[http://www.linuxhelp.net/guides/tripwire/](http://www.linuxhelp.net/guides/tripwire/)

yes, well, that page is about 10 years out of date and as such completely useless.  there is a man page for tripwire that also describes the utilities, but even those don't explain how to get it going :(

mine very thoughtfully emails me this message every day:
> tripwire[32749]: Integrity Check Failed: File could not be opened.
no idea what file that might be, or if that is causing the rest to fail, or anything at all about it.

---

### Post by Rubi1200 on 2010-07-04
From the Ubuntu Security sticky by bodhi.zazen:

[http://www.alwanza.com/howTo/linux/tripwire.html](http://www.alwanza.com/howTo/linux/tripwire.html)

[http://remoteadmin.org.uk/tutorials/42-linux/56-tripwire-ubuntu](http://remoteadmin.org.uk/tutorials/42-linux/56-tripwire-ubuntu)

---

### Post by bodhi.zazen on 2010-07-04
> **spikoley said:**
> I am looking for Tripwire HowTo with Ubuntu.  The ones I have found online do not explain the config file or how to get Tripwire to send email alerts.  It would be great if somebody wrote an Ubuntu specific Tripwire Howto.

I posted several links in my security stickies.

Read down to the tripwire section of this post:

[http://ubuntuforums.org/showpost.php?p=9265535&postcount=2](http://ubuntuforums.org/showpost.php?p=9265535&postcount=2)

Edit: oops, [Rubi1200]("http://ubuntuforums.org/member.php?u=1040746") beat me to it by a long shot ... :redface:

---

### Post by sprosty on 2010-11-30
Tripwire installs exim for smtp so it can email you. 

I had a strange problem where emails sent via exim on the command line worked fine, such as...

[FONT=Courier New]exim -i [EMAIL="joe@example.com"]joe@example.com[/EMAIL]
hello joe
CTRL-D[/FONT]

However test emails from tripwire did not. 

I eventually searched my exim logs in /var/log/exim4/mainlog and noticed that I was receiving 550 Verification failed errors such as this...

[FONT=Courier New]SMTP error from remote mail server after RCPT TO:<me@foo.edu>: host mx.foo.edu 
[123.123.123.123]: 550-Verification failed for <tripwire@myhost>\n550-Unrouteable address\n550 
Sender verify failed[/FONT]

As you can see, the sender is set to tripwire@myhost instead of [EMAIL="tripwire@myhost.foo.edu"]tripwire@myhost.foo.edu[/EMAIL]

I had the hostname on my server set to myhost which isn't a FQDN. So I changed it to myhost.foo.edu and it now works.

EDIT: Please note since tripwire uses HOSTNAME to name various files, you will no longer be able to perform checks without renaming your hostname-local.key file as well as the hostname.twd file to reflect your new hostname. 

After renaming you will face an error: Policy file does not match policy used to create database.

I decided to re-initialize the database with: 

$ sudo tripwire -m i

and now running: 

$ sudo tripwire --check

work correctly.

---

