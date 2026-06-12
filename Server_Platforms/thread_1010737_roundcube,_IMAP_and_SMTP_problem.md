---
title: "roundcube, IMAP and SMTP problem"
date: 2008-12-14
forum: Server Platforms
---

### Post by pqangel on 2008-12-14
hi, i've been trying to install a mail server for the past 4 days
may i say it was my first time doing it on a linux box
i've read and tried about 10 tutorials or more, i've mix instrucions from several places i had to start from scratch about 4 or 5 times and i just can't get the thing to work...

i have no idea where to start, all i know is i want my system running virtual users (for added security) on a mysql DB with roundcube as the webmail interface.

so far i was trying to configure SMTP and IMAP with postfix and courier (respectively) .

my box is a LAMP with ubuntu 8.10 (LAMP as in Linux, Apache, Mysql, Php) but i've got the other three missing.

also security is a must in this case :p

as i have no idea where to start i would be really thankful if you could explain step by step what and why we are doing it (not too much if you don't want to, google is my friend ;) )

thank you very much and greets

---

### Post by joenieburg on 2008-12-14
This link got it all together.
[http://ubuntuforums.org/showthread.php?t=1003560&highlight=roundcube]("http://ubuntuforums.org/showthread.php?t=1003560&highlight=roundcube")

First setup a server with security. (the Perfect server)

Then install roundcube.

But how to get virtual users? That one I cant help you.

I have it running with 8.10 on a pentium III 500 mhz and 500 MB memory.

Goodluck

---

### Post by pqangel on 2008-12-15
thank you :)

i'll get to it and tell you the results....

although so far i have to problems :(

first one is no matter what postfix won't run any service, although when i do /etc/inet.d/postfix start (or restart or stop or reload) it says eberything is ok but when i try to connect to 25 it says unable to connect if i run nmap localhost 25 is not there and if i do postfix status it says the server is not running althogh init.d said it was ok :(


thanks for the help :guitar:

---

