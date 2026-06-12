---
title: "mail server"
date: 2013-11-14
forum: Server Platforms
---

### Post by salmendar on 2013-11-14
i am trying to make a mailing server on ubuntu 13.04

i have installed postfix,maildir and devcot... settings are pattached.

after going in corcles for over 15 days my boss has given me 12 hrs to make it work or else i am out.... he doesnt pay me and this is my internship which really matters as this is the last month... please help me make it work

also sudo service dovecot restart or any such commands dont run that can restart dovecot doesnt work. i have also installed mutt and squirrel mail to test it and all attempts that i have tried have failed... please help me out.

 this is my last resort[ATTACH]247820[/ATTACH][ATTACH]247821[/ATTACH][ATTACH]247822[/ATTACH]

---

### Post by Habitual on 2013-11-14
Have a look at [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by salmendar on 2013-11-14
i have seen this and this is how i configured the post fix... i used ubuntu docs to configure all of them but still my log file says no SSL authenication

i made my own TSL certificate with the details given in ubuntu docs.

also the myhostname should have 

myhostname = server1.anttechsolutions.com     or
myhostname = anttechsolutions.com

---

### Post by salmendar on 2013-11-14
my squireel mail says i cant connect to IMAP server

---

### Post by nerdtron on 2013-11-15
Mail Server? Why not use a 1 click install?
Sorry for pointing out again. I would like to promote it since it works well for our company and for me too since since it is very easy to install and administer.
[http://www.iredmail.org/](http://www.iredmail.org/)

---

### Post by salmendar on 2013-11-17
ired mail.... that's the best solution.

thank you nerdtron.

---

### Post by nerdtron on 2013-11-17
Glad you sorted it out. Don't forget to post in the forums of iRedmail in case you have problems. The developer is very active answering questions there.

---

