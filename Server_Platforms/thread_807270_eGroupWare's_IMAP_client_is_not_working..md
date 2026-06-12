---
title: "eGroupWare's IMAP client is not working."
date: 2008-05-25
forum: Server Platforms
---

### Post by cviniciusm on 2008-05-25
Hello,

My eGroupWare's IMAP client is not working.

I'm using Ubuntu server 8.04 LTS with Postfix and Dovecot (SMTP, POP3 and IMAP).

Any ideas, please?


TIA,
cviniciusm.

---

### Post by cviniciusm on 2008-05-31
Hello,

Never mind.

E-GroupWare's mail is working fine.

I just had to create users with valid e-mail's to start send/receive e-mail.

Regards,
cviniciusm.

---

### Post by ronnieredd on 2008-08-24
I've fighting with this for awhile. Postfix, Dovecot, squirrelmail and roundcube all work fine. I cannot seem to get the imap function of egroupware to work. I"ve tried fqdn and localhost in the on the setup section for imap, however every time I try to connect (click on the felamimail link) I get:

The connection to the IMAP Server failed!!

Connection failed to localhost,143: Connection refused

or

The connection to the IMAP Server failed!!

Connection failed to myhostname.tld,143: Connection refused

---

### Post by kjurkic on 2008-09-03
On a similar note, during the installation of egroupware, on the web page for the intial install I get:

[I]"Warning Checking extension imap is loaded or loadable: False
The imap extension is needed by the two email apps (even if you use email with pop3 as protocoll)."[/I]

Did you see the same message during install? I was doing a step-by-step from here:

[http://www.ubuntugeek.com/egroupware-web-based-groupware-suite-setup.html](http://www.ubuntugeek.com/egroupware-web-based-groupware-suite-setup.html)

but since the Ubuntu server I installed already had full LAMP with mail, I was under the impression that I could skip the postfix/mailx install, as I have seen too many installs collapse when trying to overlay services over existing.

Any fixes/suggestions anyone?

TIA
Ken
PS at egroupware,
[http://www.egroupware.org/index.php?page_name=wiki&wikipage=ManualSetupCheck_install](http://www.egroupware.org/index.php?page_name=wiki&wikipage=ManualSetupCheck_install)

they had this comment:
[I]"[egw:setup/dep.png]  Checking extension imap is loaded or loadable: False
The extension imap (php extension) is needed by both email programs (even if you use the POP3-protocol).

Under Windows, all php extensions must be explicitly loaded in the php.ini file. To do this, remove the semi-colon '";"' from in front of the corresponding line, 'extension=php_imap.dll'.
Under Linux, the php extensions are usually individual packages, that is, for 'imap' the package 'php(4|5)_imap' must be installed. "[/I]

but I triple-checked, and I have php5-imap installed

---

### Post by digitalviolence on 2008-09-09
I also get the IMAP is not enabled in PHP5 problem. But it is! 

Any ideas/input appreciated.

---

### Post by ifelseif on 2008-09-28
If you install egroupware on a server with the following command:

apt-get install egroupware

Make sure to also do a:

/etc/init.d/apache2 force-reload

as the php5-imap is installed after the apache2 server is restarted and will not be loaded. The installation should be change so that the server is reloaded at the end of install.

This corrects the problem:

"Warning Checking extension imap is loaded or loadable: False
The imap extension is needed by the two email apps (even if you use email with pop3 as protocoll)."

---

