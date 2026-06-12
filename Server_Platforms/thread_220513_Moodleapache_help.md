---
title: "Moodle/apache help"
date: 2006-07-21
forum: Server Platforms
---

### Post by sdixon on 2006-07-21
Hello,

Im sure this is a quick and simple fix for the more experienced admins out there, however this is my first experience with Apache/moodle.

Ok I am running Ubuntu 6.06 and have downloaded and installed Apache2, Mysql, and PHP5.  I have even got into Moodle and configured my front page and setup some users. Problem is I cannot access the moodle page from any clients, only from [http://localhost/moodle](http://localhost/moodle).   
I suspect that all I need to do is edit the config.php

but Im not what I need to change these values to:

$CFG->wwwroot = 'http://localhost/moodle'; 
$CFG->dirroot = '/usr/share/moodle'; 
$CFG->dataroot = '/var/lib/moodle'

can I make the needed changes here or do I need to download moodle, extract it to /www and then reinstall it?  I used apt-get to install moodle and by default it put it into /usr/share/

Thanks in advance,
Shawn

---

### Post by quinreis on 2007-05-30
I have exactly the same issue with a standard install of moodle on feisy edubuntu server. Still trying, but I suspect thast the problem is more likely to be with the apache config.
Quinton

---

