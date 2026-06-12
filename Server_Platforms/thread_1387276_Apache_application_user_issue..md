---
title: "Apache application user issue."
date: 2010-01-21
forum: Server Platforms
---

### Post by caroeber on 2010-01-21
[FONT=Times New Roman][SIZE=2]I have an issue with apache not running as the protected users that has been setup.
Environment:
System: Ubuntu 8.04.3 LTS
Apache: Apache/2.2.8 (Ubuntu)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]5 website running on their own IP address.
envvars:
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]Default conf.
<VirtualHost 10.0.1.1:80>
        with AssignUserId from apache2.conf and thus envvars.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]the four sub sites confs:
<VirtualHost 10.0.0.1:80>
       AssignUserId UserID1 UserID1
<VirtualHost 10.0.0.2:80>
       AssignUserId UserID2 UserID2
<VirtualHost 10.0.0.3:80>
       AssignUserId UserID3 UserID3
The Secure site
<VirtualHost 10.0.0.4:80>
       AssignUserId UserID4 UserID4
<VirtualHost 10.0.0.4:443>
       AssignUserId UserID4 UserID4[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]Which I have tested the configuration by # out he AssignUserId.
I have installed apt-get install apache2-mpm-itk as per other recommendations.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]And still when I check the processess
# ps auwwfx | grep apache
root       402  0.0  0.3  21504  6984 ?        Ss   10:59   0:00 /usr/sbin/apache2 -k start
root      1578  0.0  0.1  21504  3508 ?        S    10:59   0:00  \_ /usr/sbin/apache2 -k start
root      1579  0.0  0.1  21504  3508 ?        S    10:59   0:00  \_ /usr/sbin/apache2 -k start
root      6692  0.0  0.1  21504  3512 ?        S    11:05   0:00  \_ /usr/sbin/apache2 -k start[/SIZE][/FONT]

[FONT=Times New Roman][SIZE=2]And not the user ID of www-data or any of the others, Any Help Please.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]All users are built and accessable via sudo for develpment purposes.[/SIZE][/FONT]

---

