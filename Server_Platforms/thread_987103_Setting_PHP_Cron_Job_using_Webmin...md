---
title: "Setting PHP Cron Job using Webmin.."
date: 2008-11-19
forum: Server Platforms
---

### Post by GodsDead on 2008-11-19
Hey there, i have a ubuntu server with lamp installed alongside Webmin, and i realized that webmin picked up a cron server YAY! 
So i have a php script that i wish to run, i guessed at how to setup the "command" and it dosunt work, so can someone please put me right!
this is what i have that does not work
(im not sure where PHP is installed..)
```

/usr/bin/php -q /var/www/cron/get_ip.php 

```
and its schedualed to 

Simple schedule .. Daily (at midnight)



This would be ausom to get running, cheers.

Tom

---

### Post by Philio on 2008-11-19
Have you checked your script is running correctly?

If you run:

/usr/bin/php -q /var/www/cron/get_ip.php

from shell does it execute correctly?

If not, you might have the path/filename incorrect, check that it is correct.

If this runs correctly I would try using:

crontab -l

This will display the crontab for the current user, you may need to prefix it with sudo to see root's crontab:

sudo crontab -l

I would also suggest you do not put your cron job scripts in /var/www especially if your server is public. The cron runs cli php and does not require the scripts to be in the web root. If your server is public someone could run your script over the web which I doubt you would want.

Final thing, which I'm not sure if you need or not but sure someone could clarify, you might need the php-cli package, install with:

sudo apt-get install php5-cli

---

### Post by GodsDead on 2008-11-19
Thanks for your quick and detailed reply, i tested out the script via the terminal, and it ran, but it ran with errors, and the reason it wouldnt run Via the terminal was because i had the script interact with a file that i didnt give a complete path too! 

But im going to definitally take your idea and move it from the wordwide area!

cheers!

---

