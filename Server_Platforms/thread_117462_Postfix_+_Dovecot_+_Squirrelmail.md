---
title: "Postfix + Dovecot + Squirrelmail"
date: 2006-01-14
forum: Server Platforms
---

### Post by s0c0 on 2006-01-14
I recently installed these three packages the other day.  Never had a problem with them on Fedora Core, but I cant seem to get Postfix working.  Dovecot is working fine as my POP3 though.  I am able to send local messages to local users and that is it.  Here is my /etc/postifx/main.cf file:

> 
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = kernel.xnsolutions.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = kernel.xnsolutions.net, localhost.xnsolutions.net, , localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all


Based on that the only thing I can think of is that my relay host is not defined.  I have tried adding yahoo (which does my dns hosting), but nothing seems to work.  Here is the read out from my /var/log/mail.log file:

> 
Jan 14 21:25:00 kernel postfix/pickup[6922]: 0A6EA1FC1F: uid=0 from=<root>
Jan 14 21:25:00 kernel postfix/cleanup[6967]: 0A6EA1FC1F: message-id=<20060115042500.0A6EA1FC1F@kernel.xnsolutions.net>
Jan 14 21:25:00 kernel postfix/qmgr[6923]: 0A6EA1FC1F: from=<root@kernel.xnsolutions.net>, size=307, nrcpt=1 (queue active)
Jan 14 21:25:20 kernel postfix/smtp[6968]: 0A6EA1FC1F: to=<chrisnizzardini@yahoo.com>, relay=none, delay=20, status=deferred (Host or domain name not found. Name service error for name=yahoo.com type=MX: Host not found, try again)


In the /var/log/mail.err file the following error repeats itself several times:

> 
Jan 13 19:54:31 kernel postfix/smtpd[2509]: fatal: no SASL authentication mechanisms


Do I have to have SMTP authentication enabled?  I know it's a smart way of doing this, but I was going to get the smtp service working first and then work in authentication.  Please advise.

As for squirrelmail.  I don't even know how to create a url for it.  On fedoracore after installing it you would just type yourserver.com/webmail, this does not seem to be the case for debian based systems.

---

### Post by bluefrog on 2006-01-16
[http://www.howtoforge.com/taxonomy_menu/1/4](http://www.howtoforge.com/taxonomy_menu/1/4)

you are not obliged to use the mysql part (so just skip mysql setup)

For dovecot you need to fiddle the dovecot conf and enble maildir in postfix as well.

james

---

### Post by Glut on 2006-01-18
The errors in mail.log indicate a DNS issue, if you do: dig -t MX yahoo.com
you should get a decent amount of responses. Otherwise you have a problem.

For the second message, if you're not going to use your SMTP server for sending outside your own subnet, turn off sasl. Its cheap and doesn't get to the root of the problem (checked libsasl2-modules is installed?) but in the short term (assuming that you're time limited) it will work.

Sorry, I don't use squirrelmail.

---

### Post by admlv on 2006-01-18
about error in mail.log I suggest you to check dns. in the error is quit enought clear written that your server can't fing yahoo.com. Make sure that you had correct nameserver defined in your settup and that firewall isn't blocking dns requests to that nameserver.

---

### Post by MJN on 2006-01-18
I recently did a combined move from RedHat to (K)ubuntu and Postfix-UWIMAP-SquirrelMail to Postfix-Dovecot-Squirrelmail and still have a good recollection of the necessary config to get it all working so should be able to help you out...

Firstly, let's take a few steps back - what exactly do you mean by '..but nothing seems to work'? You say you can send mail between local users - presumably you've been doing this with a mail client as opposed to manually telnetting to port 25? The latter can be a good way to help fault find as you don't have the isolation of a client.

From your logs, and as mentioned by the others, Postfix is (understandably) trying to get the MX records for yahoo.com. What do you get if you do a 'dig yahoo.com MX' ? Does it resolve?

If Postfix can't resolve names then it could well be due to it being run in a chroot jail. If so, try 'cp -p /etc/resolv.conf /var/spool/postfix/etc/resolv.conf' and reload/restart Postfix. (N.B. I may need to check these locations as this was my Red Hat structure)

Incidentally, you mentioned POP3 - did you know Squirrelmail only works with IMAP mailboxes? I'd be surprised if you really wanted to use POP3 as it doesn't support globally-accessible mailboxes/folder and multiple access from different clients (i.e. you might want to use Thunderbird at home, and Squirrelmail whilst away).

Also, although you probably knew this, your Postfix config is far from complete with regards to security etc... although let's cover one step at a time!

Mathew

P.S. When I'm at home I could post my config files if they're of any use/interest?
P.P.S. Stick with it - you know it'll be worth it in the end!

---

