---
title: "Installing PHP PEAR Mail"
date: 2016-02-20
forum: Server Platforms
---

### Post by SchnappiJedi on 2016-02-20
Hi,

Trying to get a Tectite formmail ([http://www.tectite.com/](http://www.tectite.com/)) script to work on Ubtuntu 14 LTS server. Script uses PHP PEAR mail to send using SMTP settings on another server ([http://www.tectite.com/fmdoc/pear_settings.php](http://www.tectite.com/fmdoc/pear_settings.php)).

First was getting this error after running "sudo apt-get install php-pear":
[I]
[Sat Feb 20 15:15:25.255224 2016] [:error] [pid ....] [client IP:64264] PHP Fatal error:  require_once(): Failed opening required 'Mail.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/... on line ..., referer: [https://.](https://.)..[/I]

Ran "sudo pear install mail" and got:

[I]WARNING: channel "pear.php.net" has updated its protocols, use "pear channel-update pear.php.net" to update
Did not download optional dependencies: pear/Net_SMTP, use --alldeps to download automatically
pear/Mail can optionally use package "pear/Net_SMTP" (version >= 1.4.1)
downloading Mail-1.3.0.tgz ...
Starting to download Mail-1.3.0.tgz (23,110 bytes)
........done: 23,110 bytes
could not extract the package.xml file from "/build/php5-0LI9sl/php5-5.5.9+dfsg/pear-build-download/Mail-1.3.0.tgz"
Download of "pear/mail" succeeded, but it is not a valid package archive
Error: cannot download "pear/Mail"
Download failed
install failed
[/I]
Can anyone offer assistance/ help in getting PHP PEAR mail installed? Let me know if need PHP version or server specifications or anything else.

---

### Post by SchnappiJedi on 2016-02-21
Tried "sudo pear channel-update pear.php.net" as well and this did nothing (error is slightly different than before after using this command see below):

[I]Did not download optional dependencies: pear/Net_SMTP, use --alldeps to download automatically
pear/Mail can optionally use package "pear/Net_SMTP" (version >= 1.4.1)
downloading Mail-1.3.0.tgz ...
Starting to download Mail-1.3.0.tgz (23,110 bytes)
........done: 23,110 bytes
could not extract the package.xml file from "/build/php5-0LI9sl/php5-5.5.9+dfsg/pear-build-download/Mail-1.3.0.tgz"
Download of "pear/Mail" succeeded, but it is not a valid package archive
Error: cannot download "pear/Mail"[/I]

---

### Post by SchnappiJedi on 2016-03-03
Never did get PHP Pear installed so installed Postfix and set it up as a SMTP relay. Used the following three tutorials to get it totally working encase anyone else runs into this in the future:

[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-14-04)
[https://www.linode.com/docs/email/postfix/postfix-smtp-debian7](https://www.linode.com/docs/email/postfix/postfix-smtp-debian7)
[http://www.cyberciti.biz/tips/howto-postfix-masquerade-change-email-mail-address.html](http://www.cyberciti.biz/tips/howto-postfix-masquerade-change-email-mail-address.html)

---

