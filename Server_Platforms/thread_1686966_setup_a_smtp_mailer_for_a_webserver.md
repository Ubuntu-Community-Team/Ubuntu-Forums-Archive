---
title: "setup a smtp mailer for a webserver"
date: 2011-02-13
forum: Server Platforms
---

### Post by mansonthomas on 2011-02-13
Hi,

  I've several webserver (ubuntu 10.10 x64) on which I would like to be able to send mail like newsletter...

  I don't need to recieve mail on these servers, I'm using google Apps for recieving mail for the hosted domains.

  There's sendmail installed by default on ubuntu server...

  Previoulsy I was using Exim4 configured to use gmail SMTP server to send technical mails (apticron, logwatch, cron mail), but it doesn't fit for newsletter type of mailing.

  On my tries, I've wanted to setup Exim4 (just for the sending part, no inbox, and not using gmail stmp) which result in : 


[LIST]
[*]sendmail marked a uninstalled but still there and working
[*]Exim4 complaining about not being able to bind the port 25
[/LIST]

I've removed exim4 (/etc/init.d/exim4 were not deleted...)
I've reinstalled sendmail

I got this warning on installof sendmail : 

/etc/mail/aliases: 5 aliases, longest 21 bytes, 91 bytes total

Warning: 1 database(s) sources
        were not found, (but were created)
        please investigate.
 * Starting Mail Transport Agent (MTA) sendmail
   ...done.

thomas@box01:/etc/init.d$ sudo service sendmail status
MSP: is run via cron (20m)
**MTA: is not running**
QUE: Same as MTA

well... it's the only thing I want to work...


the mail command is not installed on the system anymore...


Well : 


[LIST]
[*]How do I restore a working sendmail ?
[*]What do I need to do so that mail sent from these servers aren't marked as spam? (not considering the content of the mail, but the server that send the mail) I see that some company used some specialized company like "[COLOR=#000000][FONT=Times New Roman][COLOR=#777777][FONT=arial][COLOR=Black]grosbill.[/COLOR][COLOR=Black]emailingoptin.com for grosbill.com" Should I specialize one domain for all newsletter ?[/COLOR]
[/FONT][/COLOR][/FONT][/COLOR]
[/LIST]


Thanks for your help
Thomas

---

### Post by elico on 2011-02-13
apt-get install postfix

---

### Post by mansonthomas on 2011-02-13
a bit short for an answer...

I only need to sendmail (and not recieving) so why installing all the postfix stack...

---

### Post by SeijiSensei on 2011-02-13
See if apt-get purge, and maybe a repo update, help:

```

sudo apt-get update
sudo apt-get purge sendmail sendmail-*
sudo apt-get purge exim exim-*
sudo apt-get install sendmail

```

---

### Post by elico on 2011-02-13
you can indeed install only sendmail but any ubuntu server comes with postfix and postfix is an alternative to sendmail.
postfix is only for sending email.

---

