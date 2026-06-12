---
title: "Setting up Roundcube"
date: 2009-02-01
forum: Server Platforms
---

### Post by Eviltechie on 2009-02-01
I want to set up roundcube on a mail server. So far I have done a default LAMP install and have installed postfix (#apt-get install postfix). Does anyone have step by step instructions on what else I need to do to get roundcube working?

---

### Post by Poleh on 2009-02-02
if you follow the install docs that come with roundcube it's very simple - and in fact with the latest version of roundcube they have a web-based installer that does all the hard work for you.

It does assume:

1. You have a working Mail/IMAP server
2. You have a working Apache server where you can install roundcube
3. You have a working Mysql server which roundcube can use.

They also have manual install docs in the roundcube install docs so have a read there to get all you need.

[http://trac.roundcube.net/wiki/Howto_Install](http://trac.roundcube.net/wiki/Howto_Install)

---

### Post by Eviltechie on 2009-02-02
Yeah, mySQL and Apache, PHP are easy. I just don't know how to set up the mail server part.

---

### Post by Poleh on 2009-02-03
> **Eviltechie said:**
> Yeah, mySQL and Apache, PHP are easy. I just don't know how to set up the mail server part.

check out this link, it's a great setup I used to build my mail/apache/mysql server and I knew very little about Linux at the time (still a n00b, but getting there!)

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

it goes beyond just mail server install but has a very good postfix/mail server platform section - and it is still applicable to more current versions of ubunty than 7.10 so give it a go.

---

### Post by jamesrfla on 2009-02-03
Round Cube looks like a cool mail server although I use Citadel mail server. It looks like it has some kind of Macintosh interface.

---

### Post by Poleh on 2009-02-04
> **jamesrfla said:**
> Round Cube looks like a cool mail server although I use Citadel mail server. It looks like it has some kind of Macintosh interface.

Just to clarify, Roundcube is NOT a mail server - it's an IMAP webmail application that needs an underlying mail server infrastructure in place. And it looks a bit Mac-ish because it's skinnable and the guy who develops it works on a Mac :)

---

### Post by Eviltechie on 2009-02-04
I did get it working.

First you need to install postfix, then dovecot, then download roundcube and set it up. localhost works for most of the values.

---

### Post by jamesrfla on 2009-02-05
> **Poleh said:**
> Just to clarify, Roundcube is NOT a mail server - it's an IMAP webmail application that needs an underlying mail server infrastructure in place. And it looks a bit Mac-ish because it's skinnable and the guy who develops it works on a Mac :)

Thanks for letting me know what was the right definition for it. ;):)

---

