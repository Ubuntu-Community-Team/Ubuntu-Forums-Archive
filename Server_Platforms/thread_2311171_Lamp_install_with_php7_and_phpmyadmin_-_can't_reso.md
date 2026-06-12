---
title: "Lamp install with php7 and phpmyadmin - can't resolve dependencies properly"
date: 2016-01-25
forum: Server Platforms
---

### Post by spectatorx on 2016-01-25
I'm getting odd issue, i have added these ppas:
ppa:ondrej/php
ppa:nijel/phpmyadmin
I entered into terminal command to install php, mysql, phpmyadmin and other things and... this is how it went:
> 

spectator@Arena-fighter5:~$ sudo apt-get install php7.0-common php7.0-cli php7.0-fpm php7.0-curl php7.0-sqlite3 php7.0-json php7.0-tidy php7.0-mysql mysql-server phpmyadmin
[sudo] password for spectator: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 php7.0-cli : Breaks: php5-cli (< 5.6.16+dfsg-4~) but 5.6.11+dfsg-1ubuntu3.1 is to be installed
 php7.0-common : Conflicts: php5-common (< 5.6.16+dfsg-4~) but 5.6.11+dfsg-1ubuntu3.1 is to be installed
E: Unable to correct problems, you have held broken packages.





How, using ppas, can i install php7 and phpmyadmin? Did i do something wrong here? How to satisfy these dependencies? I'm not fan of manual installation as it is not proper resolution to problems with install software from ppas.

---

### Post by howefield on 2016-01-25
Thread moved to the "*Server Platforms*" sub forum for better support.

---

### Post by darkod on 2016-01-25
I am no expert on packages but it says it conflicts php5 so maybe you need to remove php5 before installing php7. In all cases, the question for the dependencies should go to the PPA author, since it wasn't Canonical that developed that php7 package(s).

---

### Post by Habitual on 2016-01-25
Backup.

---

### Post by MAFoElffen on 2016-01-25
I can see looking at PHP7. It was released only last month, but promises twice the performance over previous versions. 

But... What was your choice to use that PPA?

I saw this this morning as I was heading out the door. I talked with some of my colleagues today... and they recommended a more popular, supported and accepted PPA:
[https://launchpad.net/~ondrej/+archive/ubuntu/php](https://launchpad.net/~ondrej/+archive/ubuntu/php)

My disclaimer... as PPA's go, they are dev and need testing. They are not without problems. The release upstream was only less than a month ago. But the owner of the PPA I linked to, did support earlier versions of PHP packaging for use with Ubuntu in his PPA's, so had experience getting it to work. (so more likely of a success). I am told that there are tutorials out there, to get PHP7 going that point to and refer to that Linked PPA. So people have got there using it. So if you are testing this, before this version's official release in Ubuntu... and like living on the edge...

---

