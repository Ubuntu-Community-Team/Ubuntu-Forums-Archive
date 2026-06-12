---
title: "Postfix + MySQL - One last problem"
date: 2007-03-22
forum: Server Platforms
---

### Post by cfyves on 2007-03-22
Hi there.

Since my last posts about my auth problems with Postfix and MySQL, I've completely reinstalled the OS (since it really doesn't take long) and started over.

I used this how-to as a guide to install  Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + Roundcube + Postgrey

[http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/")

I had a couple of problems with amavis and spamassassin and found the solutions with the help of Google. (one error being a typo)

At this point, I also installed a webmail to help me test. 

I can receive email to local mailboxes if I telnet in and send an email like this:
> 
telnet localhost 25 # 
reponse back: 
> 
> 
> 
EHLO mail.domain.tld 
> 
> 
>
MAIL FROM: <email1@address.com> 
> 250 Ok 
RCPT TO: <email2@address.com> 
> 250 Ok 
data 
> 354 End data with <CR><LF>.<CR><LF></LF></CR></LF></CR> 
blah blah blah more blah 
. 
> 250 Ok;
quit 
> 221 BYE


I can also send from a local account to another local account through the webmail.

I cannot send an email to an external address. 
I get this in my mail.info file:
> 
Mar 22 15:05:46 ubuntu postfix/qmgr[4438]: warning: unexpected end-of-input from private/smtp socket while reading input attribute name
Mar 22 15:05:46 ubuntu postfix/qmgr[4438]: warning: private/smtp socket: malformed response

Mar 22 15:05:46 ubuntu postfix/qmgr[4444]: 5CA7FC7435F: to=<myemail@gmail.com>, relay=none, delay=300, status=deferred (delivery temporarily suspended: mail transport unavailable)



Any ideas?

Thanks!

---

### Post by cfyves on 2007-03-23
I'm trying to run a few checks.

This is what I get for amavis debug

> 
Trying to run amavisd-new in debug mode...
Mar 23 09:45:22 ubuntu.rdeeipe.ca /usr/sbin/amavisd-new[6912]: starting.  /usr/sbin/amavisd-new at ubuntu.rdeeipe.ca amavisd-new-2.3.3 (20050822), Unicode aware, LANG=en_CA.UTF-8
Mar 23 09:45:22 ubuntu.rdeeipe.ca /usr/sbin/amavisd-new[6912]: user=, EUID: 0 (0);  group=, EGID: 0 0 (0 0)
Mar 23 09:45:22 ubuntu.rdeeipe.ca /usr/sbin/amavisd-new[6912]: Perl version               5.008007
Mar 23 09:45:23 ubuntu.rdeeipe.ca /usr/sbin/amavisd-new[6912]: INFO: no optional modules: Sys::Hostname::Long Razor2::Client::Agent Mail::SpamAssassin::Plugin::DomainKeys Mail::DomainKeys::Header Mail::DomainKeys::Message Mail::DomainKeys::Policy Mail::DomainKeys::Signature Mail::DomainKeys::Key Mail::DomainKeys::Key::Public Crypt::OpenSSL::RSA auto::Crypt::OpenSSL::RSA::_new auto::Crypt::OpenSSL::RSA::DESTROY auto::Crypt::OpenSSL::RSA::load_public_key auto::Crypt::OpenSSL::RSA::new_public_key IP::Country::Fast
Pid_file already exists for running process (4013)... aborting
Mar 23 09:45:23 ubuntu.rdeeipe.ca /usr/sbin/amavisd-new[6912]: Net::Server: 2007/03/23-09:45:23 Pid_file already exists for running process (4013)... aborting\n\n  at line 261 in file /usr/share/perl5/Net/Server.pm
Mar 23 09:45:23 ubuntu.rdeeipe.ca /usr/sbin/amavisd-new[6912]: Net::Server: 2007/03/23-09:45:23 Server closing!


So I'm assuming that it's running properly.

---

