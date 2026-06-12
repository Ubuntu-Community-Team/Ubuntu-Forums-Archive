---
title: "Ubuntu Mail Server"
date: 2006-08-12
forum: Server Platforms
---

### Post by involutaryhaxor on 2006-08-12
Alright, I know that something similar has been posted, but it goes through the whole installation. I just want instructions for how to setup a mailserver on an already existing Ubuntu LAMP server. I don't know what I'd have to get, so if you could give me the whole thing is gory detail that woudl be great. 

Thanks in advance.

---

### Post by lvanderree on 2006-08-13
Try looking for postfix the default smtp-mail server for ubuntu, (SASL for authentication with your laptop on remote locations)
courier for imap/pop (of dovecat if you don't like it), 
squirrelmail for webmail, 
and amavis-new with clamav (virusscan) and spammassasin for filtering

I think already enough can be found about this:
[http://postfixwiki.org/](http://postfixwiki.org/)

---

### Post by slakkie on 2006-08-13
Have a look on the Ubuntu wiki: [https://wiki.ubuntu.com/?action=fullsearch&context=180&value=postfix&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=postfix&titlesearch=Titles)

I think you want to start with this one: [https://wiki.ubuntu.com/PostfixBasicSetupHowto](https://wiki.ubuntu.com/PostfixBasicSetupHowto)

---

### Post by StarQuake on 2006-08-13
I like mailscanner for mailscanning instead of amavisd:

[https://help.ubuntu.com/community/MailScanner](https://help.ubuntu.com/community/MailScanner)

---

### Post by threeten on 2006-08-14
[http://howtoforge.org/perfect_setup_ubuntu_6.06](http://howtoforge.org/perfect_setup_ubuntu_6.06)

---

### Post by involutaryhaxor on 2006-08-15
any alternatives I an use to postfix? It doesn't seem to like my server.

root@lamp-ubuntu:~# apt-get install postfix
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  postfix-mysql postfix-pgsql postfix-ldap postfix-pcre
Recommended packages:
  mail-reader resolvconf
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/923kB of archives.
After unpacking 2224kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package postfix.
(Reading database ... 21584 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.2.10-1ubuntu0.1_i386.deb) ...
Setting up postfix (2.2.10-1ubuntu0.1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: lamp-ubuntu.hsd1.ct.comcast.net.
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: lamp-ubuntu.hsd1.ct.comcast.net.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

