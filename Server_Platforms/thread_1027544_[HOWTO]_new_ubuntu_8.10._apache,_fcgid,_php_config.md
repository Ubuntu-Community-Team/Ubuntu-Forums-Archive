---
title: "[HOWTO] new ubuntu 8.10. apache, fcgid, php configuration"
date: 2009-01-01
forum: Server Platforms
---

### Post by q.dinar on 2009-01-01
hello.
(the problem is already solved, this is just a little tutorial.)
i have installed new ubuntu 8.10 cd.
and have installed apache-worker, php-cgi, fcgid. (and mysql.)
i have searched how to configure fcgid and php and apache.
and have found this tutorial:

[http://typo3.org/development/articles/using-php-with-mod-fcgid/page/3/](http://typo3.org/development/articles/using-php-with-mod-fcgid/page/3/) (by Michael Stucki).

(i opened it with typo3.org/development/articles/using-php-with-mod-fcgid/?tx_rlmpofficedocuments_pi1[view]=single&cHash=45a565e1de url which is all pages in one, better, but i do not understand its parameters.)
i made that 3 to 6 (last) items. (of "configuration" chapter.)
but it has not worked.
i thinked all needed mods are here.
then i made
"Additional configuration" (of that tutorial), 1-2-3-4, 1-2-3.
but then on apache restart it said
Invalid command 'SuexecUserGroup' ...
then i looked at /etc/apache2/mods-enabled directory with
ls /etc/apache2/mods-enabled
again and have found out that suexec is not here. i made link from /sites-available/
then again apache said on restart an error message:
Invalid command 'Action', perhaps misspelled or defined by a module not included in the server configuration
i made links for it too.
then i restarted and it has begun to work.

now i think that if there was not

<IfModule mod_actions.c>

line in /etc/apache2/conf.d/php-fcgid.conf

i would see the problem earlier.

by the way. if you make links from files in sites-available to sites-enabled with nautilus, it gives name "link to actions.conf" that will not work, link should not include spaces i think. i have seen this problem once, not now. this time i made link this way:
first looked what are available and what are enabled:

ls /etc/apache2/mods-available/

then

ls /etc/apache2/mods-enabled/

then

sudo ln -s /etc/apache2/mods-available/actions.conf /etc/apache2/mods-enabled/actions.conf
sudo ln -s /etc/apache2/mods-available/actions.load /etc/apache2/mods-enabled/actions.load

. but just now i have thought there is shorter way but needed to learn, that is in that tutorial: a2enmod actions

that should be

sudo a2enmod actions

i think. i have not tried it yet.

another "by the way":
in ubuntu 8.10 suexec is in separate package apache2-suexec . in older version i used ubuntu 7.10 it was in common apache package.>3th january 2009: i have checked that by asking in [irc://irc.freenode.net/apache](irc://irc.freenode.net/apache) (#apache channel on irc.freenode.net irc server).<

another tip:
when in synaptic check apache2, apache2-mpm-prefork is checked automatically by default (in ubuntu 8.10). but if you want to install php-cgi, checking apache2-mpm-worker instead of it is better as i know.

now i am going to/want to configure xcache.

---

### Post by q.dinar on 2009-01-01
i first installed fastcgi. i selected that because its last modification time was newer. but then have seen bug reports when searching a tutorial for it. the bug is this: when some main process is killed its child processes are not killed and so used memory increases. i have seen that some fix for it is made, may be that last modification is that. it was said that that is cosmetic modification. and fixes with cron jobs were suggested in bug trackers. as i am not advanced linux user i selected fcgid then.

---

### Post by q.dinar on 2009-01-01
i install xcache just because i have used it once, last server installation. that time i read comparisons of accelerators. i remember "apc", "eaccelerator" also. one of them is php's. "php's own" accelerator is also was said that is fast as i remember. that time i used apache module php, not cgi.

before i configured fast cgi php i configured iptables (firewall) this time. there is also a topic about that: [http://ubuntuforums.org/showthread.php?t=1022671](http://ubuntuforums.org/showthread.php?t=1022671) .

before i installed ubuntu i tried debian (etch rc6) this time. but i have seen an mysql bug that it could not be installed because "localhost" network interface was not running after installation and a strange bug that "restart" button did not work, and i disliked that user switching did not work also, but they worked just after installation, and user switching asked password two times, though it is because it is available to login to second session of same user. (also i dislike that spiral with blood color in default screensaver.)

---

### Post by q.dinar on 2009-01-04
i could not make that working with

SuexecUserGroup xxx xxx

is set in vhost.

i did not make alias as in [http://typo3.org/development/articles/using-php-with-mod-fcgid/page/4/](http://typo3.org/development/articles/using-php-with-mod-fcgid/page/4/) :

Alias /fcgi-bin/ /var/www/fcgi-bin.d/php<version>-<username>/

instead of it i made fcgi-bin directory in vhost root directory.
that did not work.

then i made alias and it started to work.

---

### Post by q.dinar on 2009-01-04
hello.
then another problem appeared.
i made other virtualhost.

i made fcgi-bin directory and executable php-fcgi-wrapper in /home/username/... :

Alias /fcgi-bin/ /home/xxxxxx/public_html/fcgi-bin/

that did not work.
in suexec.log was said:

command not in docroot (/home/xxxxxx/public_html/fcgi-bin/php-fcgi-wrapper)

so it means other docroot, not he vhost's docroot, i have thought. and tried to create php-fcgi-wrapper with needed user and group in var/www/ :

Alias /fcgi-bin/ /var/www/fcgi-bin.d/xxxxxx/

and it started to work. and i have thought that /var/www/fcgi-bin.d directory also should be user=xxxxxx and group=xxxxxx (not only "php-fcgi-wrapper" "sh" script in it) .

by the way there is "apache2-suexec-custom" package of ubuntu 8.10.
description of apache2-suexec:

Provides the standard suexec helper program for mod_suexec. This version is compiled with document root /var/www and userdir suffix public_html. If you need different settings, use the package apache2-suexec-custom.

---

