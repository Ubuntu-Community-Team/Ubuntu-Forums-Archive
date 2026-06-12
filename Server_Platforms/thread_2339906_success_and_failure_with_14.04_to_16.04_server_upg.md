---
title: "success and failure with 14.04 to 16.04 server upgrade"
date: 2016-10-13
forum: Server Platforms
---

### Post by Bushcraft Bill on 2016-10-13
I think the upgrade was 90% success as I my wordpress sites still work but my PHPBB3 3.1 did not make it through the upgrade I am having an error here is what I got any idea if its something that needs fixing or tweaking for me with ubuntu like did I miss something in the upgrade or is their now a fault with my phpbb3 3.1 forum

===============
General Error
SQL ERROR [ mysqli ]

Expression #6 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'forum1.p.post_time' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by [1055]

SQL

SELECT u.username, u.user_id, u.user_colour, u.user_type, p.poster_id, p.post_time, COUNT(p.post_id) AS total_posts FROM phpbb_users u, phpbb_posts p WHERE u.user_id > 1 AND u.user_id = p.poster_id AND (u.user_type <> 3) AND u.user_id NOT IN (2, 48) AND p.post_time BETWEEN 1475280000 AND 1476415605 GROUP BY u.user_id ORDER BY total_posts DESC, p.post_time DESC, p.post_id DESC LIMIT 1

BACKTRACE

FILE: (not given by php)
LINE: (not given by php)
CALL: msg_handler()

FILE: [ROOT]/phpbb/db/driver/driver.php
LINE: 855
CALL: trigger_error()

FILE: [ROOT]/phpbb/db/driver/mysqli.php
LINE: 193
CALL: phpbb\db\driver\driver->sql_error()

FILE: [ROOT]/phpbb/db/driver/mysql_base.php
LINE: 45
CALL: phpbb\db\driver\mysqli->sql_query()

FILE: [ROOT]/phpbb/db/driver/driver.php
LINE: 261
CALL: phpbb\db\driver\mysql_base->_sql_query_limit()

FILE: [ROOT]/phpbb/db/driver/factory.php
LINE: 321
CALL: phpbb\db\driver\driver->sql_query_limit()

FILE: [ROOT]/ext/threedi/tpotm/event/listener.php
LINE: 125
CALL: phpbb\db\driver\factory->sql_query_limit()

FILE: (not given by php)
LINE: (not given by php)
CALL: threedi\tpotm\event\listener->display_tpotm()

FILE: [ROOT]/vendor/symfony/event-dispatcher/Symfony/Component/EventDispatcher/EventDispatcher.php
LINE: 158
CALL: call_user_func()

FILE: [ROOT]/vendor/symfony/event-dispatcher/Symfony/Component/EventDispatcher/EventDispatcher.php
LINE: 46
CALL: Symfony\Component\EventDispatcher\EventDispatcher->doDispatch()

FILE: [ROOT]/phpbb/event/dispatcher.php
LINE: 60
CALL: Symfony\Component\EventDispatcher\EventDispatcher->dispatch()

FILE: [ROOT]/phpbb/event/dispatcher.php
LINE: 46
CALL: phpbb\event\dispatcher->dispatch()

FILE: [ROOT]/includes/functions.php
LINE: 5421
CALL: phpbb\event\dispatcher->trigger_event()

FILE: [ROOT]/index.php
LINE: 240
CALL: page_footer()
Please notify the board administrator or webmaster:

---

### Post by Vegan on 2016-10-14
i use wordpress and i learned from using my old IBM box that distribution upgrades often mangled the system

now that i am using cloud virtual machines when a new major LTS surfaces, i create a new VM and migrate, when done i chuck the old VM

try running
[COLOR="#FF0000"]
sudo apt update
sudo apt full-upgrade[/COLOR]

---

### Post by Bushcraft Bill on 2016-10-14
I have not tried setting up a cloud virtual machine yet I will look into it once I can get 16.04 working with my forum..
I will try the sudo update/upgrade thing I may have missed doing that now that I think about it thanks....

---

### Post by Bushcraft Bill on 2016-10-14
did not work comes back with ignoring file invalid filename extension for both update and upgrade oh well was worth the try maybe its done different in 16.04

---

### Post by darkod on 2016-10-14
I don't know if you were aware, but 16.04 uses PHP7 instead of PHP5 like earlier versions of ubuntu. And an upgrade does NOT automatically install php* packages that websites might use. One of the more important is for example php7.0-mysql that manages mysql connections (the old package was php5-mysql).

So you might need to go over your documentation and see what are you using from php5 and install the appropriate package for php7.0. And this still might not help completely if there are any sites that work only in php5. They will need to be redone for php7 I guess.

---

### Post by Bushcraft Bill on 2016-10-14
darko you hit the nail on the head my problem is PHP7 my software does not support it so I am hooped for now, So guess mystery is solved for now LOL....

---

### Post by cariboo on 2016-10-15
If your sites can run with php 5.6 it will run along side php 7. Check out this thread:

[http://askubuntu.com/questions/761713/how-can-i-downgrade-from-php-7-to-php-5-6-on-ubuntu-16-04](http://askubuntu.com/questions/761713/how-can-i-downgrade-from-php-7-to-php-5-6-on-ubuntu-16-04)

---

### Post by Bushcraft Bill on 2016-10-15
Thanks for that I think I will leave things alone I have a working 16.04 right now and dont want to jinks things also they are upgrading the software for the forum so I will wait till thats done.

---

