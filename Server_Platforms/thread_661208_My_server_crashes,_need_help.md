---
title: "My server crashes, need help?"
date: 2008-01-07
forum: Server Platforms
---

### Post by Mr-Heier on 2008-01-07
Hey guys!
Latly my server has started to crash. I run apache2 and mysql with Vbulletin forum.

Suddenly the load hits load number 100 and the server is so slow i have to reboot it to make it usable again. Then it is okay for a couple of days just to crash again.

Were do i start to look for errors? How can i check the logs, what should i look for?

Thanks in advance.

:(

---

### Post by xeth_delta on 2008-01-07
To check CPU/memory utilization by programs use in a command line **top**.

You will be able to find system messages and logs by calling **dmesg** and reading **/var/log/messages**. You will find many other log files in **/var/log**.

For instance:
```
sudo cat /var/log/messages
```
Xeth

---

### Post by zipperback on 2008-01-07
System log files are in /var/log

Are you also running a mail server on your system? If so, what does the load on the system in regard to the mail server say?

Check your mail server logs and see if someone is using your system as some sort of open relay for spam.

Also, when your system is at 100% load, don't reboot, just kill apache and see if the load goes down. If you killed apache and the load stays at 100% then you probably have problems elsewhere on the box.

I would also check your box for a root kit of some sort.

- zipperback
:popcorn:

---

### Post by Mr-Heier on 2008-01-07
In my Apache2 log this says before crashing.

server reached MaxClients setting, consider raising the MaxClients setting

---

### Post by Mr-Heier on 2008-01-07
> **zipperback said:**
> System log files are in /var/log

Are you also running a mail server on your system? If so, what does the load on the system in regard to the mail server say?

Check your mail server logs and see if someone is using your system as some sort of open relay for spam.

Also, when your system is at 100% load, don't reboot, just kill apache and see if the load goes down. If you killed apache and the load stays at 100% then you probably have problems elsewhere on the box.

I would also check your box for a root kit of some sort.

- zipperback
:popcorn:

I dont have a mailserver running. How do i look for a rootkit?

---

### Post by zipperback on 2008-01-07
> **Mr-Heier said:**
> In my Apache2 log this says before crashing.

server reached MaxClients setting, consider raising the MaxClients setting


What do you have your MaxClients set to?

- zipperback
:popcorn:

---

### Post by Mr-Heier on 2008-01-07
> **zipperback said:**
> What do you have your MaxClients set to?

- zipperback
:popcorn:

I cant find maxclients setting in php.ini. Or my apache2 conf. I only find somethinhg simillar.

Max Requests 	Per Child: 1000 - Keep Alive: on - Max Per Connection: 100

---

### Post by Mr-Heier on 2008-01-07
hmm since i run Zend it uses another apache 2 config file.

/usr/local/Zend/etc/php.ini 

In that php.ini file i cannot find the maxclients. Tough when i check the original apache2.conf file i find it and its set to 150.

It also says this in the config. 

Scan this dir for additional .ini files /etc/php5/apache2/conf.d 

Does this mean that it also uses the config from the old apache2 conf file?

---

