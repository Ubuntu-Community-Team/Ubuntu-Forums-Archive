---
title: "mysql :: user privilege corruption forcing --skip-grant-tables"
date: 2008-03-17
forum: Server Platforms
---

### Post by bowmanr on 2008-03-17
good day,

posted this on the mysql forums, no response, wondering if anyone here has got a clue please ...

<previouspost>
good day,

a question from a complete mysql newbie here.

my server running mysql (linux, ubuntu, fiesty) experienced a brownout which had rather a negative impact on my user rights system table. now, i can only run the mysq daemon with 'mysqld --skip-grant-tables &'. this i've added to rc.local. not an ideal solution really.

is there anyway to force mysql to rebuild the user rights system table?

on a completely different machine, i tried installing mysql-server, setting the root password to something specifc, and then purging the mysql install with 'sudo aptitude purge mysql-server'. however, when i subsequently reinstalled mysql-server, the root password remained as per the previous install. i therefore infer from this that a simple remove and reinstall won't necessarily fix the corruption. maybe someone could let me know what else i need to manually remove between the purge and install commands?

thanks for any thoughts and advice
robert bowman
</previouspost>

the following link i found has been helpfull : [http://bookmarks.honewatson.com/2008/03/06/purge-mysql-ubuntu-feisty-gutsy/](http://bookmarks.honewatson.com/2008/03/06/purge-mysql-ubuntu-feisty-gutsy/)

from the info in the above link, i've written a script which will dump databases, purge mysql-server, reinstall mysql, rebuild database. this script successfully resolves the issue on a test box under gutsy. however, on the live server, the "sudo apt-get –purge remove mysql-server mysql-common mysql-client" command insists on removing additional software which is dependent on mysql. a reasonable thing todo, certainly ... however, i REALLY do not want to have to reinstall everything else again! arrrgh! i changed apt-get to aptitude and discovered the gui which allows selection of removals, but it kept mentioning downgrading packages etc...

can i prevent this behaviour please? is it possible to remove mysql-server and it's dependencies, but not remove ANYTHING dependent on mysql-server. therefore, keeping the server in it's current software configured state post the reinstall and fix to mysql???

or alternatively, can anyone think of a way of acheiving part one of what i posted to mysql -- in essence "how can i force a rebuild of the system database responsible for user privileges?".

thanks for your thoughts
robert

---

### Post by bowmanr on 2008-03-20
if it helps, i've just taken the attached screenshot of mysql-admin looking at the mysql schema. not sure i like the look of them 'Incorrect file format' messages!!

any thoughts please?
robert

---

