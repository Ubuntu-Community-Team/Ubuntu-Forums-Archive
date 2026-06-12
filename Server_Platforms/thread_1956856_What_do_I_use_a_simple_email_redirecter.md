---
title: "What do I use a simple email redirecter"
date: 2012-04-11
forum: Server Platforms
---

### Post by wpflum on 2012-04-11
Here are the specifics, I use a Verizon email account to send and receive email but I redirect email to me through a domain name I own.  So if someone sends an email to [email]myemail@myemail.com[/email] the site redirects it to my Verizon account [email]myemail@verizon.com[/email] which I then get using Outlook.  This way I can have multiple emails like [email]hisemail@myemail.com[/email] and [email]heremail@myemail.com[/email] which all get redirected to the one Verizon account then I have Outlook sort these into separate folders based on the sent to address.  

What I want to do is set up an email server??? or something that will go out and get all of the emails from the Verizon server every couple of minutes and then sort them into separate accounts and allow a pop/smtp server into each specific email account to read and send from.  This way I can have separate computers with their own Outlooks send and receive the individual accounts and be able to virus scan, spam block it and monitor the different email addresses.  The last part is the important part as we let the kids have email addresses of their own that I routinely monitor to try and keep them out of trouble.

Any suggestions on a package or packages I should look at and directions on configuring it/them?

Thanks

---

### Post by SeijiSensei on 2012-04-11
[Fetchmail]("http://fetchmail.berlios.de/") is designed for this task.  You can set it up to collect the mail from the common inbox at Verizon and deliver the messages to the proper users on a local server.  You probably also want to install [ClamAV]("http://www.clamav.net/") and [SpamAssassin]("http://spamassassin.apache.org/") on the local server as well.  

All of these are in the repositories.

---

### Post by wpflum on 2012-04-12
> **SeijiSensei said:**
> [Fetchmail]("http://fetchmail.berlios.de/") is designed for this task.  You can set it up to collect the mail from the common inbox at Verizon and deliver the messages to the proper users on a local server.  You probably also want to install [ClamAV]("http://www.clamav.net/") and [SpamAssassin]("http://spamassassin.apache.org/") on the local server as well.  

All of these are in the repositories.

Looks good but I haven't seen info on splitting up the incoming emails into different users mailboxes.  Lots about combining multiple email accounts into a single one on the server but nothing the other way unless I'm asking the wrong things in the Google search.  :oops:

Anyone direct me to something that will let me run a perl script or something else that can take the single email account emails and put them in separate system email accounts based on the TO field of the email??

---

### Post by wpflum on 2012-04-12
Should have waited a bit before posting, I looked further down in the man pages for fetchmail and it seems that I can use a 'TO' to do something like


poll mail.verizon.net
with protocol POP3
user UNAME
with password PASSWORD,
to 'kid1@myemail.com'='Kid1_on_server'
to 'kid2@myemail.com'='Kid2_on_server'
to 'kid3@myemail.com'='Kid3_on_server'
to *='main_account_on_server'

Not sure about the last one but I want everything other than the first three accounts to go to a single account I'll access from my main pc.

I'm guessing I run this from the root account?? Or should I make up an incoming email account login and use that?

The other thing I'd like to know and I haven't figured out yet is can I use the same setup but add multiple destination users??

Something like  

to 'kid1@myemail.com'='Kid1_on_server','Monitor_on_server'

So I can get a copy of all emails into their addresses.

Last but not least I want to add a Spam blocker and virus scanner to the mix but I'll wait till I can get the system working the way I want it to first before attempting the rest.

Suggestions??

---

### Post by SeijiSensei on 2012-04-12
> **wpflum said:**
> I'm guessing I run this from the root account?? Or should I make up an incoming email account login and use that?

I'd run it as root via [cron]("https://help.ubuntu.com/community/CronHowto"), either by using "sudo crontab -e" to create an entry in /var/spool/cron/root, or by editing the system-wide crontab /etc/crontab.

> The other thing I'd like to know and I haven't figured out yet is can I use the same setup but add multiple destination users??

The easiest way to do this is to create mail aliases.  You're going to need to run a "mail transfer agent" like Postfix (the Ubuntu default) or sendmail on the box as well as fetchmail.  Fetchmail will download the mail from Verizon then hand the messages over to the MTA for delivery.  For deliveries to multiple accounts, you'd just add entries to [/etc/aliases]("http://linux.die.net/man/5/aliases.postfix") like this:

```
me-and-kid1:   kid1, me
```

then tell fetchmail to deliver kid1's mail to me-and-kid1 rather than kid1 alone.  (Both sendmail and Postfix use the same alias format.) The MTA will handle expanding the alias and delivering the message to both the "me" and "kid1" mailboxes.

For the spam/virus scanning, I'd actually suggest installing [MailScanner]("http://www.mailscanner.info/").  It's a very large program written in Perl that accepts the inbound mail, scans it for viruses and spam, and routes the messages according to policies you specify.  For instance, it will quarantine messages containing viruses, and tag or quarantine spams.  It has a large array of options, so it might be overkill for you, but once it's set up it works wonderfully.  I've been using it for about a decade now on both my own servers and on servers I manage for clients.

You might also want to install [procmail]("http://www.procmail.org/"), which replaces the local "mail delivery agent" in sendmail or Postfix.  Procmail lets you write "recipes" that route mail based on regular expressions in the headers or body.  It's an incredibly powerful toolkit for mail handling though the syntax for the recipes is a bit arcane.  There are two useful man pages that come with procmail; "[man procmailrc]("http://linux.die.net/man/5/procmailrc")" describes the recipe syntax and "[man procmailex]("http://linux.die.net/man/5/procmailex")" offers many helpful examples.

All of these programs are in the Ubuntu repositories.

---

