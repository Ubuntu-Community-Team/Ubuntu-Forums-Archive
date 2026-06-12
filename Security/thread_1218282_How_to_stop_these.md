---
title: "How to stop these?"
date: 2009-07-20
forum: Security
---

### Post by zemon_ on 2009-07-20
In my apache error logs I get these errors.

```
[Mon Jul 20 04:58:00 2009] [error] [client 72.249.191.83] File does not exist: /var/www/webmail2
[Mon Jul 20 04:58:03 2009] [error] [client 72.249.191.83] File does not exist: /var/www/roundcubemail
[Mon Jul 20 04:58:03 2009] [error] [client 72.249.191.83] File does not exist: /var/www/rcmail
[Mon Jul 20 04:58:04 2009] [error] [client 72.249.191.83] File does not exist: /var/www/CHANGELOG
[Mon Jul 20 04:58:04 2009] [error] [client 72.249.191.83] File does not exist: /var/www/rc
[Mon Jul 20 04:58:04 2009] [error] [client 72.249.191.83] File does not exist: /var/www/email
[Mon Jul 20 04:58:05 2009] [error] [client 72.249.191.83] File does not exist: /var/www/mail2
[Mon Jul 20 04:58:05 2009] [error] [client 72.249.191.83] File does not exist: /var/www/Webmail
[Mon Jul 20 04:58:05 2009] [error] [client 72.249.191.83] File does not exist: /var/www/components
[Mon Jul 20 04:58:05 2009] [error] [client 72.249.191.83] File does not exist: /var/www/joomla
[Mon Jul 20 04:58:06 2009] [error] [client 72.249.191.83] File does not exist: /var/www/squirrelmail
[Mon Jul 20 04:58:06 2009] [error] [client 72.249.191.83] File does not exist: /var/www/vhcs2
[Mon Jul 20 04:58:06 2009] [error] [client 72.249.191.83] File does not exist: /var/www/round
[Mon Jul 20 04:58:07 2009] [error] [client 72.249.191.83] File does not exist: /var/www/mailweb

```

Is there a way to automatically add the ip to iptables block list when that ip requests a page for example "mailweb"

---

### Post by keithweddell on 2009-07-20
You can use fail2ban or denyhosts to do this.  You might have to play with the regexes to get them to recognise this specific log message.

Keith

---

### Post by bodhi.zazen on 2009-07-20
```
sudo iptables -A INPUT -s 72.249.191.83 -j DROP
```[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

denyhosts will not work it adds the ip to /etc/hosts.deny (tcp wrapper), which apache does not honor.

Furthermore there are no log in attempts.

[http://blog.bodhizazen.net/linux/how-to-blacklist-an-ip-address-in-apache/](http://blog.bodhizazen.net/linux/how-to-blacklist-an-ip-address-in-apache/)

You could also [http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/](http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/)

although mod_security may be more hassle then it is worth (you will have to modify the rules).

Edit : fail2ban might work , but you would have to write a regex to search your logs. 404 errors are quite common and you probably do not want to ban ip based on 404 errors in the logs. Careful you do not lock yourself out with that, lol.

---

### Post by zemon_ on 2009-07-20
Thanks for the answers:)

I have installed fail2ban not sure whether the part of the fail2ban config is correct.

```
# Fail2Ban configuration file
#
# Author: Cyril Jaquier
#
# $Revision: 629 $
#

[Definition]

# Option:  loglevel
# Notes.:  Set the log level output.
#          1 = ERROR
#          2 = WARN
#          3 = INFO
#          4 = DEBUG
# Values:  NUM  Default:  3
#
loglevel = 3

# Option:  logtarget
# Notes.:  Set the log target. This could be a file, SYSLOG, STDERR or STDOUT.
#          Only one log target can be specified.
# Values:  STDOUT STDERR SYSLOG file  Default:  /var/log/fail2ban.log
#
logtarget = /var/log/fail2ban.log

# Option: socket
# Notes.: Set the socket file. This is used to communicate with the daemon. Do
#         not remove this file when Fail2ban runs. It will not be possible to
#         communicate with the server afterwards.
# Values: FILE  Default:  /var/run/fail2ban/fail2ban.sock
#
socket = /var/run/fail2ban/fail2ban.sock

failregex = [[]client (?P<host>\S*)[]] File does not exist: .*\.php

```

Is this correct?

---

